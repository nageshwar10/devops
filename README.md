# Terraform Learning Roadmap

## Absolute Zero → Good Terraform Level → AWS → Production → Senior/Architect

> **Purpose:** Build deep Terraform expertise first. AWS and real infrastructure projects begin only after the core Terraform language, execution model, state, modules, dependencies, lifecycle, refactoring, testing, and troubleshooting are understood well.
>
> **Learning principle:** Terraform first. Cloud provider second. Production architecture last.
>
> **Roadmap only:** This document defines what to learn and in what order. It does not teach the topics.

---

# Learning Path

```text
PHASE 1
Terraform Fundamentals
        ↓
PHASE 2
HCL & Terraform Language
        ↓
PHASE 3
Terraform Core Concepts
        ↓
PHASE 4
Expressions, Functions & Dynamic Configuration
        ↓
PHASE 5
Dependencies & Resource Lifecycle
        ↓
PHASE 6
Terraform State & Backends
        ↓
PHASE 7
Modules & Reusability
        ↓
PHASE 8
Environments, Workspaces & Configuration Architecture
        ↓
PHASE 9
Import, Drift & Refactoring
        ↓
PHASE 10
Terraform Testing, Debugging & Quality
        ↓
        ★ SOLID TERRAFORM LEVEL ★
        ↓
PHASE 11
AWS Provider Fundamentals
        ↓
PHASE 12
Terraform + AWS Infrastructure
        ↓
PHASE 13
Production AWS Infrastructure
        ↓
PHASE 14
Security & Governance
        ↓
PHASE 15
Terraform CI/CD
        ↓
PHASE 16
Multi-Account & Multi-Region AWS
        ↓
PHASE 17
Terraform at Scale
        ↓
PHASE 18
Senior / Architect-Level Terraform
        ↓
FINAL
Production-Grade Capstone
```

---

# Phase 1 — Terraform Fundamentals

## Chapter 1 — Infrastructure as Code

### Topics

* What is Infrastructure as Code?
* Why Infrastructure as Code exists
* Imperative vs declarative infrastructure
* Desired state
* Configuration drift
* Idempotency
* Reproducibility
* Version-controlled infrastructure
* Immutable vs mutable infrastructure
* Infrastructure lifecycle
* Benefits and limitations of IaC
* Terraform's role in IaC

### Learning Objective

Understand the problem Terraform is solving before learning Terraform syntax.

### Exercise

* Identify examples of imperative and declarative infrastructure.
* Describe infrastructure drift scenarios.
* Design a simple infrastructure lifecycle without writing Terraform.

---

## Chapter 2 — What Is Terraform?

### Topics

* What Terraform is
* What Terraform is not
* Terraform's core purpose
* Terraform workflow
* Terraform configuration
* Terraform state
* Providers
* Resources
* Data sources
* Modules
* Backend
* Terraform Registry
* Terraform CLI

### Terraform Workflow

```text
Configuration
      ↓
terraform init
      ↓
terraform validate
      ↓
terraform plan
      ↓
terraform apply
      ↓
Infrastructure
```

### Exercise

* Install Terraform.
* Verify the installation.
* Run basic Terraform CLI commands.
* Create a minimal Terraform configuration.
* Initialize it.
* Validate it.
* Generate a plan.
* Apply it.
* Destroy it.

---

## Chapter 3 — Terraform Architecture

### Topics

* Terraform CLI architecture
* Terraform Core
* Provider plugins
* Configuration
* State
* Backend
* Dependency graph
* Planning engine
* Apply engine
* Provider API interaction
* Terraform Registry
* Local vs remote execution

### Learning Objective

Be able to explain what happens when:

```text
terraform plan
```

and:

```text
terraform apply
```

are executed.

---

# Phase 2 — HCL & Terraform Language

## Chapter 4 — HCL Fundamentals

### Topics

* HCL syntax
* Blocks
* Arguments
* Attributes
* Expressions
* References
* Comments
* Strings
* Numbers
* Booleans
* Lists
* Maps
* Sets
* Tuples
* Objects
* Null values

### Files

Understand the purpose and conventions of:

```text
main.tf
variables.tf
outputs.tf
locals.tf
providers.tf
versions.tf
data.tf
terraform.tfvars
```

Understand that these filenames are conventions; Terraform evaluates `.tf` files in a module directory collectively.

### Exercise

Create Terraform configurations using each major HCL type.

---

## Chapter 5 — Terraform Type System

### Topics

* Primitive types
* Complex types
* Type constraints
* Optional attributes
* Nullable values
* Type conversion
* Type inference
* Type mismatch errors

### Exercise

Create variables using:

* string
* number
* bool
* list
* set
* map
* tuple
* object

---

## Chapter 6 — Terraform Variables

### Topics

* Input variables
* Variable declarations
* Type constraints
* Defaults
* Descriptions
* Validation rules
* Sensitive variables
* Nullable variables
* Variable precedence
* `.tfvars`
* `.auto.tfvars`
* CLI variables
* Environment variables

### Exercise

Create a configuration whose behavior is controlled entirely through input variables.

---

## Chapter 7 — Locals

### Topics

* Local values
* Derived values
* Reusable expressions
* Naming conventions
* Common tags
* Reducing duplication
* Locals vs variables

### Exercise

Create reusable naming and metadata logic.

---

## Chapter 8 — Outputs

### Topics

* Output values
* Output descriptions
* Sensitive outputs
* Output dependencies
* Root module outputs
* Child module outputs

### Exercise

Expose calculated values from a Terraform configuration.

---

# Phase 3 — Terraform Core Concepts

## Chapter 9 — Resources

### Topics

* Resource blocks
* Resource arguments
* Resource attributes
* Resource addresses
* Resource instances
* Resource lifecycle
* Resource identity
* Create
* Read
* Update
* Replace
* Destroy

### Exercise

Use a provider that does not require real cloud infrastructure to practice resource concepts.

---

## Chapter 10 — Data Sources

### Topics

* What data sources are
* Resources vs data sources
* Reading external information
* Data dependencies
* Data source evaluation
* Data source limitations

### Exercise

Build a configuration that consumes external data from a provider.

---

## Chapter 11 — Providers

### Topics

* Provider architecture
* Provider configuration
* Provider requirements
* Provider versions
* Provider aliases
* Provider authentication concepts
* Provider plugins
* Provider Registry

### Exercise

Configure a non-cloud provider first and understand provider behavior before introducing AWS.

---

## Chapter 12 — Provider Versioning

### Topics

* `required_providers`
* Version constraints
* Provider upgrades
* Provider compatibility
* Dependency constraints
* `.terraform.lock.hcl`
* Provider checksums
* Reproducible provider installation

### Exercise

* Pin provider constraints.
* Generate the lock file.
* Review it.
* Perform a controlled provider upgrade.

---

# Phase 4 — Expressions, Functions & Dynamic Configuration

## Chapter 13 — Expressions

### Topics

* References
* Attribute access
* Index expressions
* Arithmetic expressions
* Comparison expressions
* Boolean expressions
* Conditional expressions
* String interpolation
* Expression evaluation
* Unknown values

### Exercise

Create increasingly complex expressions and predict their results before running Terraform.

---

## Chapter 14 — Conditional Expressions

### Topics

* Conditional operator
* Boolean conditions
* Optional configuration
* Environment-specific configuration
* Conditional resource creation

### Exercise

Create configurations that change behavior based on input values.

---

## Chapter 15 — Terraform Functions

### String Functions

* `format`
* `join`
* `split`
* `replace`
* `trim`
* `lower`
* `upper`
* `substr`

### Collection Functions

* `length`
* `concat`
* `flatten`
* `distinct`
* `sort`
* `contains`
* `merge`
* `lookup`

### Numeric Functions

* `min`
* `max`
* `ceil`
* `floor`

### Encoding Functions

* `jsonencode`
* `jsondecode`
* `yamlencode`
* `yamldecode`

### File Functions

* `file`
* `templatefile`

### Type Conversion

* `tostring`
* `tonumber`
* `tolist`
* `toset`
* `tomap`

### Exercise

Build reusable transformations using Terraform functions.

---

## Chapter 16 — Collection Expressions

### Topics

* `for` expressions
* List transformations
* Map transformations
* Filtering
* Nested expressions
* Conditional filtering
* Object construction

### Exercise

Transform complex input data into infrastructure-ready structures.

---

## Chapter 17 — `count`

### Topics

* Resource repetition
* `count.index`
* Conditional resource creation
* Resource addressing
* Index-based identity
* Limitations of `count`

### Exercise

Create multiple resource instances using `count`.

---

## Chapter 18 — `for_each`

### Topics

* Map iteration
* Set iteration
* `each.key`
* `each.value`
* Stable resource addressing
* Resource identity
* `count` vs `for_each`

### Exercise

Rewrite a `count` implementation using `for_each` and compare the resulting resource addresses.

---

## Chapter 19 — Dynamic Blocks

### Topics

* Nested blocks
* Dynamic blocks
* Iteration inside nested configuration
* When dynamic blocks are useful
* When dynamic blocks reduce readability

### Exercise

Generate nested configuration dynamically.

---

# Phase 5 — Dependencies & Resource Lifecycle

## Chapter 20 — Terraform Dependency Graph

### Topics

* Dependency graph
* Graph nodes
* Graph edges
* Implicit dependencies
* Explicit dependencies
* Parallel execution
* Dependency ordering
* Graph visualization

### Commands

```text
terraform graph
```

### Exercise

Build dependent resources and inspect the graph.

---

## Chapter 21 — Implicit Dependencies

### Topics

* Resource references
* Attribute dependencies
* Dependency inference
* Dependency propagation

### Exercise

Create configurations where dependencies are automatically inferred.

---

## Chapter 22 — Explicit Dependencies

### Topics

* `depends_on`
* When `depends_on` is necessary
* When `depends_on` is unnecessary
* Hidden dependencies
* Overusing dependencies
* Impact on parallelism

### Exercise

Create and troubleshoot an ordering problem.

---

## Chapter 23 — Resource Lifecycle

### Topics

* Resource replacement
* In-place updates
* Destruction
* Replacement triggers
* Lifecycle meta-arguments

---

## Chapter 24 — Lifecycle Meta-Arguments

### Topics

* `create_before_destroy`
* `prevent_destroy`
* `ignore_changes`
* `replace_triggered_by`

### Exercise

Simulate resource replacement and protect critical resources from accidental destruction.

---

# Phase 6 — Terraform State & Backends

## Chapter 25 — Terraform State Fundamentals

### Topics

* What state is
* Why Terraform needs state
* Desired configuration
* State
* Real infrastructure
* Resource mapping
* Resource identity
* State refresh
* State drift
* State consistency

### Core Model

```text
Configuration
      ↓
    State
      ↓
Infrastructure
```

### Exercise

Inspect Terraform state and understand how resource addresses map to infrastructure.

---

## Chapter 26 — State Commands

### Topics

* `terraform state list`
* `terraform state show`
* `terraform state pull`
* `terraform state push`
* `terraform state mv`
* `terraform state rm`

### Exercise

Practice state inspection and controlled state manipulation in a disposable environment.

---

## Chapter 27 — Local Backend

### Topics

* Local state
* State file
* State backup
* Local collaboration problems
* State locking considerations
* Limitations of local state

### Exercise

Observe what happens when Terraform state is managed locally.

---

## Chapter 28 — Remote Backends

### Topics

* Backend concept
* Remote state
* State storage
* State locking
* State encryption
* Access control
* State versioning
* Backend initialization
* Backend migration

### Exercise

Move Terraform state from local storage to a remote backend.

---

## Chapter 29 — State Security

### Topics

* Sensitive values in state
* State access
* Encryption
* Access permissions
* State backups
* State recovery
* State exposure risks

### Exercise

Identify sensitive information that can exist in state and design controls around it.

---

## Chapter 30 — State Architecture

### Topics

* One state vs multiple states
* State boundaries
* Blast radius
* Team ownership
* Environment boundaries
* Account boundaries
* Regional boundaries
* Dependency boundaries

### Exercise

Design state boundaries for a hypothetical organization without implementing cloud infrastructure.

---

# Phase 7 — Modules & Reusability

## Chapter 31 — Module Fundamentals

### Topics

* Root module
* Child modules
* Module inputs
* Module outputs
* Module source
* Module composition
* Module interfaces

### Exercise

Convert repeated Terraform configuration into a child module.

---

## Chapter 32 — Module Design

### Topics

* Single-responsibility modules
* Module boundaries
* Abstraction
* Reusability
* Inputs
* Outputs
* Validation
* Defaults
* Stable interfaces
* Avoiding over-abstraction

### Exercise

Design a module interface before writing the implementation.

---

## Chapter 33 — Module Sources

### Topics

* Local modules
* Git modules
* Registry modules
* Private modules
* Module versioning
* Module source references

---

## Chapter 34 — Module Composition

### Topics

* Module-to-module communication
* Inputs and outputs
* Module dependencies
* Module layering
* Root module orchestration

### Exercise

Build:

```text
root
 ├── module-a
 ├── module-b
 └── module-c
```

without introducing AWS.

---

## Chapter 35 — Module Versioning

### Topics

* Semantic versioning
* Module releases
* Compatibility
* Breaking changes
* Version constraints
* Upgrade strategy

---

# Phase 8 — Environments & Configuration Architecture

## Chapter 36 — Terraform Environment Strategies

### Topics

* Separate root modules
* Directory-based environments
* Shared modules
* Environment-specific configuration
* Configuration duplication
* State separation

### Exercise

Design:

```text
dev
staging
prod
```

using reusable modules.

---

## Chapter 37 — Terraform Workspaces

### Topics

* Workspace concept
* Workspace commands
* Workspace-specific state
* Workspace-specific values
* Workspace limitations
* When workspaces are appropriate
* When workspaces are not appropriate

### Exercise

Create multiple workspaces using a non-cloud provider.

---

## Chapter 38 — Workspaces vs Directory-Based Environments

### Topics

* Isolation
* State management
* Access control
* Blast radius
* CI/CD integration
* Production suitability
* Team ownership

### Exercise

Compare both approaches and document the trade-offs.

---

# Phase 9 — Import, Drift & Refactoring

## Chapter 39 — Terraform Import

### Topics

* Why imports are required
* Importing existing infrastructure
* Resource addresses
* Import blocks
* Import limitations
* Configuration generation
* Post-import cleanup

### Exercise

Create resources outside Terraform and bring them under Terraform management.

---

## Chapter 40 — Drift

### Topics

* Configuration drift
* State drift
* External modifications
* Drift detection
* Refresh
* Plan behavior
* Drift remediation

### Exercise

Modify managed resources outside Terraform and recover the desired state.

---

## Chapter 41 — Refactoring

### Topics

* Resource renaming
* Resource movement
* Module refactoring
* Resource identity
* Address changes
* `moved` blocks
* `terraform state mv`
* Avoiding unnecessary recreation

### Exercise

Move resources into modules without destroying the underlying infrastructure.

---

## Chapter 42 — Safe Infrastructure Changes

### Topics

* Reading plans
* Detecting replacements
* Destructive changes
* Blast radius
* Change sequencing
* Production change safety

### Exercise

Review intentionally dangerous plans and identify the risk before applying them.

---

# Phase 10 — Testing, Debugging & Quality

## Chapter 43 — Terraform Formatting & Validation

### Topics

* `terraform fmt`
* `terraform validate`
* Formatting standards
* Validation workflow
* CI validation

---

## Chapter 44 — Terraform Console

### Topics

* `terraform console`
* Expression evaluation
* Function testing
* Collection inspection
* Debugging expressions

### Exercise

Use the console to test complex expressions before putting them into configuration.

---

## Chapter 45 — Terraform Testing

### Topics

* Native Terraform testing
* Test files
* Test runs
* Assertions
* Test variables
* Test isolation
* Test cleanup
* Unit-style testing
* Integration-style testing

### Exercise

Write tests for reusable Terraform modules.

---

## Chapter 46 — Static Analysis

### Topics

* TFLint
* Checkov
* Trivy
* Other Terraform static analysis tools
* Security findings
* False positives
* Exceptions

### Exercise

Run multiple scanners against the same configuration and compare findings.

---

## Chapter 47 — Debugging Terraform

### Topics

* Terraform logs
* `TF_LOG`
* `TF_LOG_PATH`
* Plan inspection
* State inspection
* Graph inspection
* Provider failures
* Authentication failures
* Dependency failures
* API failures

### Exercise

Diagnose intentionally broken configurations.

---

## Chapter 48 — Terraform Troubleshooting

### Scenarios

* Invalid configuration
* Provider initialization failure
* Authentication failure
* Permission failure
* State lock
* State drift
* Resource replacement
* Import failure
* Module failure
* Provider version conflict
* Failed apply
* Partial infrastructure creation

---

# Terraform Milestone — Solid Terraform Level

At this point, **stop adding cloud-provider complexity** and verify your Terraform knowledge.

You should be able to:

* Read HCL comfortably.
* Write Terraform configurations from scratch.
* Explain Terraform's execution model.
* Explain resources and data sources.
* Use variables, locals, and outputs.
* Use functions and expressions.
* Use `count` and `for_each` correctly.
* Understand dynamic blocks.
* Explain implicit and explicit dependencies.
* Explain the dependency graph.
* Use lifecycle rules appropriately.
* Explain Terraform state deeply.
* Work with remote backends.
* Design state boundaries.
* Build reusable modules.
* Design module interfaces.
* Explain workspaces and their trade-offs.
* Import existing resources.
* Detect and resolve drift.
* Refactor resources safely.
* Write Terraform tests.
* Debug Terraform failures.
* Read and reason about Terraform plans.
* Explain why a configuration is designed a particular way.

**Only after this milestone should AWS become the primary focus.**

---

# Phase 11 — AWS Provider Fundamentals

## Chapter 49 — AWS Provider

### Topics

* AWS provider architecture
* Provider configuration
* AWS regions
* AWS profiles
* Environment credentials
* IAM role authentication
* Provider versioning
* AWS provider documentation
* Provider aliases

### Exercise

Configure Terraform against a non-production AWS account.

---

## Chapter 50 — AWS Authentication

### Topics

* AWS CLI authentication
* IAM roles
* Temporary credentials
* AssumeRole
* Environment credentials
* Profile-based authentication
* CI/CD authentication concepts
* OIDC concepts

### Security Principle

Do not build production workflows around long-lived access keys.

---

# Phase 12 — Terraform + AWS Infrastructure

## Chapter 51 — AWS Resource Fundamentals

Learn Terraform management of:

* VPC
* Subnets
* Route Tables
* Internet Gateway
* NAT Gateway
* Security Groups
* EC2
* S3
* IAM
* ECR

---

## Chapter 52 — AWS Data Sources

Learn:

* AWS account identity
* Availability Zones
* AMIs
* Existing VPCs
* Existing subnets
* Existing IAM information
* Existing AWS resources

---

## Chapter 53 — AWS Networking

Build:

```text
VPC
├── Public Subnets
│   └── Internet Gateway
│
├── Private Subnets
│   └── NAT Gateway
│
└── Route Tables
```

### Topics

* CIDR planning
* Availability Zones
* Public/private subnet design
* Route tables
* NAT
* VPC endpoints
* DNS
* Security Groups

### Project 1

**AWS VPC with Terraform**

Build a reusable VPC configuration.

---

## Chapter 54 — AWS Compute

### Topics

* EC2
* Launch Templates
* Auto Scaling Groups
* Load Balancers
* Target Groups
* User data
* IAM instance roles

### Project 2

**Highly Available AWS Web Application**

Build:

```text
Internet
   ↓
ALB
   ↓
Auto Scaling
   ↓
EC2
```

---

## Chapter 55 — AWS Storage

### Topics

* S3
* Versioning
* Encryption
* Lifecycle policies
* Bucket policies
* Access controls
* EBS
* EFS

### Project 3

**Secure S3 Platform**

Implement secure storage with encryption, versioning, lifecycle, and controlled access.

---

## Chapter 56 — AWS IAM

### Topics

* IAM users
* IAM roles
* IAM policies
* Trust policies
* Managed policies
* Inline policies
* Least privilege
* Cross-account access

### Project 4

**AWS IAM Foundation**

Create reusable IAM modules and least-privilege roles.

---

## Chapter 57 — AWS Databases

### Topics

* RDS
* Aurora
* DB subnet groups
* Parameter groups
* Encryption
* Backup
* Deletion protection
* Monitoring
* Secrets

### Project 5

**Production-Style RDS Environment**

Build a private database environment with secure access and lifecycle protections.

---

# Phase 13 — Production AWS Infrastructure

## Chapter 58 — Production Network Architecture

### Topics

* Multi-AZ design
* Public/private/isolated subnets
* VPC endpoints
* Network security
* NAT cost considerations
* DNS architecture
* Network segmentation

### Project 6

**Production AWS Network**

Create a reusable production networking module.

---

## Chapter 59 — Production Compute Architecture

### Topics

* High availability
* Auto Scaling
* Load balancing
* Health checks
* Immutable infrastructure
* Instance replacement
* Capacity planning

---

## Chapter 60 — Production Database Architecture

### Topics

* High availability
* Backups
* Recovery
* Encryption
* Maintenance
* Deletion protection
* Failover
* Disaster recovery

---

## Chapter 61 — AWS Containers

### Topics

* ECR
* ECS
* EKS
* Terraform's role in container infrastructure
* Infrastructure vs application deployment
* Terraform + Kubernetes boundaries
* GitOps boundaries

### Project 7

**AWS Container Platform**

Provision the underlying container platform using Terraform while keeping application deployment concerns separate.

---

# Phase 14 — Security & Governance

## Chapter 62 — Terraform Security

### Topics

* Secure state
* Secure credentials
* Least privilege
* Sensitive variables
* Secrets in state
* AWS Secrets Manager
* SSM Parameter Store
* Encryption
* IAM boundaries

---

## Chapter 63 — Infrastructure Security Scanning

### Topics

* TFLint
* Checkov
* Trivy
* Policy validation
* Security gates
* False-positive management

---

## Chapter 64 — Policy as Code

### Topics

* Policy as Code
* OPA
* Conftest
* Sentinel concepts
* Mandatory tags
* Approved regions
* Encryption requirements
* Public resource restrictions
* Security group restrictions

### Project 8

**Secure Terraform Governance**

Create a policy framework that blocks insecure AWS infrastructure before deployment.

---

# Phase 15 — Terraform CI/CD

## Chapter 65 — Infrastructure CI/CD

### Pipeline

```text
Pull Request
      ↓
Format
      ↓
Validate
      ↓
Lint
      ↓
Security Scan
      ↓
Test
      ↓
Terraform Plan
      ↓
Review
      ↓
Approval
      ↓
Terraform Apply
```

### Topics

* CI validation
* Plan generation
* Plan artifacts
* Apply workflows
* Approval gates
* Branch protection
* Concurrency control
* State locking

---

## Chapter 66 — AWS OIDC for CI/CD

### Topics

* OIDC
* GitHub Actions
* AWS IAM trust policies
* Short-lived credentials
* Least privilege CI roles
* Environment-specific roles

### Project 9

**Secure Terraform CI/CD**

Build a CI/CD pipeline that authenticates to AWS without long-lived AWS access keys.

---

# Phase 16 — Multi-Account & Multi-Region AWS

## Chapter 67 — AWS Organizations

### Topics

* AWS Organizations
* Management account
* Workload accounts
* Security account
* Logging account
* Shared services
* Account boundaries

---

## Chapter 68 — Multi-Account Terraform

### Topics

* Cross-account roles
* AssumeRole
* Provider aliases
* Provider passing
* Account-specific state
* Account-specific modules
* Access boundaries

### Project 10

**Multi-Account AWS Foundation**

Manage infrastructure across:

```text
Management
Security
Logging
Shared Services
Development
Staging
Production
```

---

## Chapter 69 — Multi-Region Terraform

### Topics

* Provider aliases
* Regional resources
* Global resources
* Route 53
* CloudFront
* S3
* Disaster recovery
* Regional failover

### Project 11

**Multi-Region AWS Infrastructure**

Deploy a platform across primary and secondary regions.

---

# Phase 17 — Terraform at Scale

## Chapter 70 — Large Repository Architecture

### Topics

* Monorepo
* Multi-repository
* Environment directories
* Shared modules
* Platform modules
* Ownership boundaries
* Repository boundaries

---

## Chapter 71 — State Architecture at Scale

### Topics

* State per environment
* State per account
* State per region
* State per platform component
* Blast radius
* State ownership
* Cross-state dependencies
* Remote state design

---

## Chapter 72 — Dependency Architecture

### Topics

* Cross-stack dependencies
* Remote state data
* Explicit interfaces
* Shared infrastructure
* Dependency reduction
* Avoiding dependency spaghetti

---

## Chapter 73 — Performance

### Topics

* Large plans
* State size
* Provider API limits
* Parallelism
* CI runtime
* Module complexity
* Plan optimization

---

## Chapter 74 — Terraform & Provider Upgrades

### Topics

* Terraform version upgrades
* Provider upgrades
* Module upgrades
* Lock files
* Breaking changes
* Compatibility testing
* Upgrade sequencing
* Rollback planning

---

# Phase 18 — Senior / Architect Terraform

## Chapter 75 — Terraform Internals

### Topics

* Terraform evaluation
* Planning
* Refresh
* Unknown values
* Dependency graph
* Resource instances
* State snapshots
* Provider interaction
* Plan vs apply behavior

---

## Chapter 76 — Advanced State Management

### Topics

* State recovery
* State migration
* State movement
* State corruption scenarios
* State locking incidents
* Resource identity
* Safe state manipulation

---

## Chapter 77 — Advanced Refactoring

### Topics

* Large-scale resource movement
* Module restructuring
* `moved` blocks
* State migration
* Zero-recreation refactoring
* Compatibility during migration

---

## Chapter 78 — Platform Engineering with Terraform

### Topics

* Golden modules
* Infrastructure standards
* Self-service infrastructure
* Reusable platform components
* Developer experience
* Guardrails
* Platform ownership
* Infrastructure APIs
* Internal platform patterns

---

## Chapter 79 — Terraform Governance

### Topics

* Module governance
* Versioning policy
* State ownership
* Access controls
* Review standards
* Security standards
* Production approval
* Change management
* Incident procedures
* Upgrade policy

---

## Chapter 80 — Architectural Trade-offs

Be able to reason about:

* Modules vs duplication
* Workspaces vs directories
* One state vs multiple states
* Monorepo vs multiple repositories
* Centralized vs decentralized Terraform
* Terraform vs CloudFormation
* Terraform vs Pulumi
* Terraform vs Ansible
* Terraform vs GitOps
* Terraform vs cloud-native IaC
* Local execution vs CI execution

---

# Phase 19 — Production Operations

## Chapter 81 — Change Management

### Topics

* Infrastructure change reviews
* Plan review
* Risk classification
* Approval workflows
* Production changes
* Emergency changes
* Rollback planning

---

## Chapter 82 — Disaster Recovery

### Topics

* State recovery
* Infrastructure recreation
* Backup strategy
* Multi-region recovery
* Dependency recovery order
* Recovery testing

---

## Chapter 83 — Cost Optimization

### Topics

* Infrastructure sizing
* NAT Gateway costs
* Storage costs
* RDS costs
* Environment sizing
* Ephemeral infrastructure
* Resource lifecycle
* Cost allocation tags

---

## Chapter 84 — Infrastructure Observability

### Topics

* Terraform execution logs
* CI/CD logs
* CloudTrail
* AWS Config
* CloudWatch
* Audit trails
* Change visibility

---

# Phase 20 — Real-World Progressive Projects

Projects should become progressively harder.

## Project 12 — Modular AWS Foundation

Build:

* VPC
* Subnets
* Routing
* Security Groups
* IAM
* S3

Requirements:

* Reusable modules
* Remote state
* Variables
* Outputs
* Validation
* Tests

---

## Project 13 — Multi-Environment Platform

Build:

```text
dev
staging
prod
```

Requirements:

* Shared modules
* Separate state
* Environment-specific configuration
* Environment-specific security
* Environment-specific capacity

---

## Project 14 — Production Application Platform

Build:

```text
Route 53
    ↓
CloudFront / ALB
    ↓
Compute
    ↓
RDS
    ↓
S3
```

Requirements:

* High availability
* Encryption
* IAM
* Monitoring
* Backups
* Secure state

---

## Project 15 — Multi-Account Platform

Build:

```text
Management
Security
Logging
Shared Services
Dev
Staging
Production
```

Requirements:

* Cross-account roles
* Provider aliases
* Separate state
* Reusable modules
* CI/CD
* Security policies

---

## Project 16 — Multi-Region Platform

Build:

```text
Primary Region
      │
      ├── Application
      ├── Database
      └── Storage

Secondary Region
      │
      ├── Application
      ├── Recovery
      └── Storage
```

Requirements:

* Provider aliases
* Regional infrastructure
* Disaster recovery
* Failover design
* Cost analysis

---

# Phase 21 — Production-Grade Capstone

# Capstone: Terraform AWS Platform

## Objective

Design and implement a realistic Terraform platform that demonstrates the complete skill set from this roadmap.

---

## Architecture

```text
                           Git Repository
                                │
                                ▼
                         Terraform CI/CD
                                │
             ┌──────────────────┼──────────────────┐
             │                  │                  │
          Validate           Security            Tests
             │                  │                  │
             └──────────────────┼──────────────────┘
                                │
                                ▼
                         Terraform Plan
                                │
                          Review / Approval
                                │
                                ▼
                         Terraform Apply
                                │
          ┌─────────────────────┼─────────────────────┐
          │                     │                     │
     Shared Services        Security              Logging
          │                     │                     │
          └─────────────────────┼─────────────────────┘
                                │
                     ┌──────────┴──────────┐
                     │                     │
                  Dev/Staging            Prod
                     │                     │
                     └──────────┬──────────┘
                                │
                         Multi-Region
```

---

## Capstone Requirements

### Terraform

* [ ] Modular architecture
* [ ] Strong typing
* [ ] Variable validation
* [ ] Locals
* [ ] Outputs
* [ ] Functions
* [ ] `for_each`
* [ ] Conditional configuration
* [ ] Dynamic blocks where justified
* [ ] Explicit/implicit dependencies
* [ ] Lifecycle controls
* [ ] Import capability
* [ ] Refactoring strategy
* [ ] Tests

### State

* [ ] Remote backend
* [ ] Encryption
* [ ] Versioning
* [ ] Locking
* [ ] Access control
* [ ] State recovery strategy
* [ ] Clearly defined state boundaries

### AWS

* [ ] VPC
* [ ] Multi-AZ networking
* [ ] Security Groups
* [ ] IAM
* [ ] S3
* [ ] Compute
* [ ] Load Balancer
* [ ] RDS/Aurora
* [ ] ECR
* [ ] Monitoring

### Environments

* [ ] Development
* [ ] Staging
* [ ] Production
* [ ] Environment isolation
* [ ] Environment-specific configuration

### Multi-Account

* [ ] Cross-account IAM
* [ ] Provider aliases
* [ ] Account-specific state
* [ ] Account boundaries

### Multi-Region

* [ ] Primary region
* [ ] Secondary region
* [ ] Regional provider configuration
* [ ] Disaster recovery strategy

### Security

* [ ] OIDC
* [ ] Least privilege
* [ ] No long-lived CI credentials
* [ ] Encrypted state
* [ ] Encryption at rest
* [ ] Security scanning
* [ ] Policy as code
* [ ] Mandatory tagging

### CI/CD

* [ ] Format
* [ ] Validate
* [ ] Lint
* [ ] Security scan
* [ ] Test
* [ ] Plan
* [ ] Review
* [ ] Approval
* [ ] Apply
* [ ] Concurrency control

### Documentation

Produce:

* Architecture diagram
* Repository documentation
* Module documentation
* State architecture
* Environment strategy
* Security model
* CI/CD documentation
* Disaster recovery runbook
* Troubleshooting guide
* Upgrade guide
* Operations runbook

---

# Capstone Failure & Recovery Exercises

Intentionally simulate:

1. Terraform drift
2. Failed apply
3. State lock
4. Incorrect resource rename
5. Module refactor
6. Provider upgrade
7. Resource import
8. AWS permission failure
9. CI/CD authentication failure
10. Cross-account permission failure
11. Resource deletion outside Terraform
12. Incorrect variable configuration
13. Broken module version
14. Regional failure

For each scenario:

```text
Detect
  ↓
Understand
  ↓
Assess blast radius
  ↓
Recover
  ↓
Validate
  ↓
Prevent recurrence
```

---

# Senior Interview Preparation

Interview preparation should run alongside the roadmap after the fundamentals are learned.

## Beginner

* What is Terraform?
* What is Infrastructure as Code?
* Terraform workflow
* Provider
* Resource
* Data source
* Variable
* Local
* Output
* State
* Backend
* Module
* `terraform init`
* `terraform plan`
* `terraform apply`
* `terraform destroy`

## Intermediate

* `count` vs `for_each`
* `depends_on`
* Lifecycle
* Variable precedence
* Functions
* Dynamic blocks
* Remote state
* State locking
* Workspaces
* Import
* Drift
* Modules
* Provider aliases

## Advanced

* State architecture
* State recovery
* Module design
* Refactoring
* `moved` blocks
* Multi-account AWS
* Multi-region
* Cross-account IAM
* CI/CD
* OIDC
* Testing
* Security scanning
* Policy as code
* Terraform upgrades

## Senior / Architect

Be able to design and defend:

1. Terraform architecture for hundreds of AWS accounts.
2. State boundaries for a large organization.
3. A reusable module ecosystem.
4. Secure Terraform CI/CD.
5. Cross-account authentication.
6. Multi-region infrastructure.
7. Disaster recovery for Terraform-managed infrastructure.
8. A Terraform governance model.
9. Safe large-scale refactoring.
10. Provider and Terraform upgrade strategy.
11. Blast-radius reduction strategy.
12. Platform-engineering workflows using Terraform.
13. Terraform vs alternative IaC approaches.
14. Centralized vs decentralized infrastructure management.
15. Production incident recovery involving Terraform state.

---

# Final Competency Levels

## Level 1 — Beginner

You can:

* Understand Terraform terminology.
* Write basic HCL.
* Use variables and outputs.
* Run the Terraform workflow.
* Understand resources and providers.

---

## Level 2 — Intermediate

You can:

* Write Terraform independently.
* Use expressions and functions.
* Use `count` and `for_each`.
* Build modules.
* Understand dependencies.
* Manage state.
* Use remote backends.
* Work with environments.
* Import resources.
* Detect drift.

---

## Level 3 — Advanced

You can:

* Design reusable modules.
* Refactor Terraform safely.
* Design state boundaries.
* Test Terraform.
* Debug failures.
* Manage provider versions.
* Build secure Terraform workflows.
* Design complex AWS infrastructure.

---

## Level 4 — Production

You can:

* Build production AWS infrastructure.
* Secure Terraform state.
* Implement CI/CD.
* Use OIDC.
* Manage multiple environments.
* Manage multiple AWS accounts.
* Manage multiple regions.
* Implement security and policy controls.
* Operate and recover Terraform infrastructure.

---

## Level 5 — Senior / Architect

You can:

* Design Terraform platforms at organizational scale.
* Establish module standards.
* Design state architecture.
* Reduce blast radius.
* Design multi-account and multi-region strategies.
* Establish governance.
* Design self-service infrastructure.
* Lead Terraform migrations.
* Design upgrade strategies.
* Handle Terraform incidents.
* Review architecture and code.
* Explain trade-offs and defend design decisions.

---

# Final Learning Order

```text
1. Infrastructure as Code
2. Terraform Fundamentals
3. Terraform Architecture
4. HCL
5. Terraform Types
6. Variables
7. Locals
8. Outputs
9. Resources
10. Data Sources
11. Providers
12. Provider Versioning
13. Expressions
14. Functions
15. Conditionals
16. for Expressions
17. count
18. for_each
19. Dynamic Blocks
20. Dependency Graph
21. depends_on
22. Lifecycle
23. State
24. State Commands
25. Backends
26. Remote State
27. State Security
28. State Architecture
29. Modules
30. Module Design
31. Module Composition
32. Module Versioning
33. Environments
34. Workspaces
35. Import
36. Drift
37. Refactoring
38. Testing
39. Debugging
40. Troubleshooting

        ★ SOLID TERRAFORM LEVEL ★

41. AWS Provider
42. AWS Authentication
43. AWS Resources
44. AWS Networking
45. AWS Compute
46. AWS Storage
47. AWS IAM
48. AWS Databases
49. Containers
50. Production AWS Architecture
51. Security
52. Policy as Code
53. CI/CD
54. OIDC
55. Multi-Account AWS
56. Multi-Region AWS
57. Terraform at Scale
58. Terraform Internals
59. Platform Engineering
60. Governance
61. Disaster Recovery
62. Cost Optimization
63. Senior Architecture
64. Capstone
```

---

# End State

The roadmap is complete when Terraform is no longer treated as a collection of commands or HCL syntax.

The target capability is:

```text
Understand the requirement
        ↓
Design the infrastructure
        ↓
Choose Terraform boundaries
        ↓
Design modules
        ↓
Design state
        ↓
Implement configuration
        ↓
Understand the dependency graph
        ↓
Review the plan
        ↓
Test and secure it
        ↓
Deploy through CI/CD
        ↓
Operate it
        ↓
Refactor it safely
        ↓
Recover from failures
        ↓
Scale the architecture
        ↓
Explain and defend the design
```
