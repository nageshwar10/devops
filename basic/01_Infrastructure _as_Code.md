# Chapter 1 — Infrastructure as Code

## 1. What is Infrastructure as Code?

**Infrastructure as Code (IaC)** is the practice of defining and managing infrastructure using code or configuration files instead of manually creating and configuring infrastructure.

### Example

Without IaC:

```text
Human
  ↓
AWS Console / CLI
  ↓
Infrastructure
```

With IaC:

```text
Infrastructure Code
        ↓
     IaC Tool
        ↓
Infrastructure
```

Terraform is an **IaC tool**.

> IaC is the approach/practice; Terraform is a tool used to implement it.

---

## 2. Why Infrastructure as Code Exists

IaC helps solve problems associated with manually managed infrastructure.

### Main problems

* Manual repetitive work
* Human configuration errors
* Inconsistent environments
* Difficult infrastructure reproduction
* Difficult change tracking
* Infrastructure knowledge depending on individuals
* Difficulty managing infrastructure at scale

### Example

Manually managed environments may accidentally become different:

```text
DEV
EC2 → t3.medium

STAGING
EC2 → t3.large

PROD
EC2 → t3.xlarge
```

Some differences may be intentional, but accidental differences can cause problems.

With IaC, infrastructure definitions can be standardized and reused.

---

## 3. Imperative vs Declarative Infrastructure

### Imperative

**Imperative = HOW**

You tell the system the steps it needs to perform.

```text
1. Create VPC
2. Create subnet
3. Create route table
4. Associate subnet
```

Focus:

```text
HOW to achieve the result
```

---

### Declarative

**Declarative = WHAT**

You describe the desired result.

```text
I want:

1 VPC
2 Subnets
1 Route Table
```

Focus:

```text
WHAT the final infrastructure should look like
```

---

### Simple Difference

| Imperative           | Declarative            |
| -------------------- | ---------------------- |
| HOW                  | WHAT                   |
| Defines steps        | Defines desired result |
| Focuses on procedure | Focuses on state       |
| "Do these steps"     | "I want this result"   |

Terraform primarily follows a **declarative model**.

---

## 4. Desired State

**Desired state** means the infrastructure configuration we want to exist.

Example:

```text
Desired State:

VPC
 ├── 2 Subnets
 ├── 1 Route Table
 └── 5 EC2 Instances
```

Terraform uses the configuration to determine what infrastructure should exist.

Conceptually:

```text
Desired State
      ↓
   Terraform
      ↓
Actual Infrastructure
```

### Example

If:

```text
Desired = 5 servers
Actual  = 3 servers
```

Terraform can determine that changes are required.

A `terraform plan` can show the proposed changes without actually applying them.

---

## 5. Configuration Drift

**Configuration drift** occurs when the actual infrastructure becomes different from the expected configuration.

Example:

```text
Desired:
5 servers

Actual:
4 servers
```

Someone manually deleted one server.

This creates drift:

```text
Desired ≠ Actual
```

### Common causes

* Manual changes through cloud consoles
* Manual CLI changes
* Other automation modifying infrastructure
* Resources being deleted or modified outside the expected process

### Example

Terraform configuration:

```text
instance_type = t3.medium
```

Someone manually changes the instance to:

```text
t3.large
```

Now:

```text
Terraform Configuration
        ↓
    t3.medium

Actual Infrastructure
        ↓
    t3.large
```

This is drift.

---

## 6. Idempotency

**Idempotency** means that performing the same operation multiple times produces the same intended result rather than continuously creating unintended changes.

For infrastructure:

```text
Desired:
2 servers
```

Running the infrastructure management process once:

```text
2 servers
```

Running it again should still result in:

```text
2 servers
```

not:

```text
4 servers
```

### Simple idea

```text
Apply
 ↓
Desired state achieved

Apply again
 ↓
No unnecessary changes
```

Idempotency is an important property of declarative infrastructure management.

---

## 7. Reproducibility

**Reproducibility** means being able to recreate infrastructure consistently from its defined configuration.

Example:

```text
Terraform Configuration
        ↓
       DEV
```

The same reusable configuration can help create:

```text
STAGING
PRODUCTION
```

with appropriate environment-specific values.

The goal is to avoid manually rebuilding infrastructure from memory.

---

## 8. Version-Controlled Infrastructure

Infrastructure code can be stored in a version-control system such as Git.

Example:

```text
Developer
    ↓
Modify Terraform Code
    ↓
Git Commit
    ↓
Pull Request
    ↓
Review
    ↓
Terraform Plan
    ↓
Apply
```

This provides a history of infrastructure configuration changes.

You can track:

* What changed
* Who changed it
* When it changed
* Why it changed through commits/PRs

### Example

```text
Before:
t3.medium

After:
t3.large
```

The change can be reviewed before being applied.

---

## 9. Immutable vs Mutable Infrastructure

### Mutable Infrastructure

Existing infrastructure is modified in place.

Example:

```text
Existing Server
      ↓
Upgrade / Modify
      ↓
Same Server
```

Example changes:

```text
OS upgrade
Software update
Configuration change
```

---

### Immutable Infrastructure

Instead of modifying an existing resource, a new version is created and the old resource is replaced.

```text
Old Infrastructure
       ↓
New Infrastructure
       ↓
Replace Old
```

### Simple Difference

| Mutable                        | Immutable                         |
| ------------------------------ | --------------------------------- |
| Modify existing infrastructure | Replace with new infrastructure   |
| Changes happen in place        | New version is created            |
| Server identity may remain     | New infrastructure may be created |

Terraform can support infrastructure replacement patterns, depending on the resource and configuration.

---

## 10. Infrastructure Lifecycle

Infrastructure has a lifecycle.

A simplified lifecycle is:

```text
Design
  ↓
Create
  ↓
Manage
  ↓
Modify
  ↓
Scale
  ↓
Replace
  ↓
Destroy
```

For Terraform-managed infrastructure:

```text
Configuration
      ↓
Plan
      ↓
Apply
      ↓
Infrastructure
      ↓
Changes
      ↓
Update / Replace
      ↓
Destroy
```

Infrastructure management isn't only about initial creation. It also includes **changes, updates, replacement, and removal**.

---

## 11. Benefits of IaC

### Automation

Reduces repetitive manual infrastructure operations.

### Consistency

Helps keep infrastructure configurations consistent.

### Reusability

Infrastructure definitions can be reused.

### Reproducibility

Infrastructure can be recreated from its configuration.

### Version Control

Infrastructure changes can be tracked through Git.

### Reviewability

Infrastructure changes can be reviewed before being applied.

### Scalability

Automation makes managing larger infrastructure easier.

### Reduced Manual Errors

Reduces many errors caused by repetitive manual configuration.

---

## 12. Limitations of IaC

IaC is powerful, but it doesn't automatically solve every infrastructure problem.

### Bad code can create bad infrastructure

```text
Bad IaC
   ↓
Bad Infrastructure
```

### Learning complexity

Large IaC systems can become complex.

### State management

Tools such as Terraform require state management.

### Drift can still happen

People or other systems can modify infrastructure outside the IaC workflow.

### Provider limitations

IaC tools depend on the capabilities and behavior of their providers.

### Destructive changes

Incorrect configuration can potentially cause infrastructure to be modified or destroyed.

### Operational discipline

Teams still need:

* Code reviews
* Testing
* Security controls
* Access control
* Change management

---

# 13. Terraform's Role in IaC

Terraform is an **Infrastructure as Code tool**.

It allows infrastructure requirements to be expressed using configuration.

Conceptually:

```text
Terraform Configuration
        ↓
      Terraform
        ↓
    Provider
        ↓
    Cloud API
        ↓
Infrastructure
```

For AWS:

```text
Terraform Configuration
        ↓
      Terraform
        ↓
   AWS Provider
        ↓
      AWS API
        ↓
AWS Infrastructure
```

Terraform primarily uses a **declarative approach**.

You describe:

```text
WHAT infrastructure you want
```

Terraform determines:

```text
WHAT changes are required
```

to move the infrastructure toward that desired configuration.

---

# 14. Key Concepts to Remember

```text
IaC
→ Infrastructure defined using code/configuration

Imperative
→ HOW

Declarative
→ WHAT

Desired State
→ What we want the infrastructure to look like

Drift
→ Actual infrastructure differs from expected configuration

Idempotency
→ Repeated execution produces the same intended result

Reproducibility
→ Infrastructure can be recreated consistently

Version Control
→ Infrastructure changes can be tracked through Git

Mutable
→ Modify existing infrastructure

Immutable
→ Replace infrastructure with a new version

Terraform
→ IaC tool using a primarily declarative model
```

---

# Chapter 1 Mental Model

Keep this overall picture in mind:

```text
                 Infrastructure as Code
                         │
                         ▼
              Define Infrastructure
                    as Code
                         │
                         ▼
                  Desired State
                         │
                         ▼
                     Terraform
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
           Compare              Determine
           current               changes
           state                    │
              └──────────┬──────────┘
                         ▼
                   Terraform Plan
                         │
                         ▼
                    Apply Changes
                         │
                         ▼
                  Real Infrastructure
```

## Chapter 1 — Core Takeaway

> **Infrastructure as Code allows infrastructure to be defined, managed, reproduced, reviewed, and changed through code and automation instead of relying primarily on manual configuration. Terraform implements this approach using a primarily declarative model based around desired infrastructure configuration.**
