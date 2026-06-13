# Specialized Cloud Red Teaming Roadmap: Target Enterprise Cloud Infrastructure

---

## ⛅ Phase 1: Cloud Architecture & Identity Foundations
*Before you can simulate attacks against corporate cloud tenants, you must understand how modern multi-cloud networks manage identity, access policies, and resources.*

### Core Architectural Concepts to Master
*   **Identity and Access Management (IAM)**: Master the core components of Cloud Security—Users, Groups, Roles, Policies, Service Accounts, and Identity Providers (IdP).
*   **The Shared Responsibility Model**: Understand exactly what security controls are managed by the cloud provider versus what the enterprise client is responsible for configuring.
*   **Metadata Services (IMDS)**: Learn how virtual machines dynamically retrieve operational data from the cloud backbone (IMDSv1 vs. IMDSv2).
*   **Core Services (The Big Three)**:
    *   **AWS**: IAM, S3, EC2, Lambda, EKS, CloudTrail.
    *   **Azure / Entra ID**: Microsoft Entra ID (formerly Azure AD), App Registrations, Key Vaults, Azure Functions, Resource Groups.
    *   **GCP**: Cloud IAM, Compute Engine, GCS, Cloud Functions, GKE.

### Best Free Training Resources
*   **AWS Certified Cloud Practitioner** / **Azure Fundamentals (AZ-900)**: Study the official free documentation and video prep modules to learn foundational cloud vocabulary.
*   **fwd:cloudsec Presentations**: Watch past technical conference presentations on YouTube to understand emerging cloud security architectures.

---

## 🔓 Phase 2: Initial Access & Cloud Enumeration
*Learn how to gain an initial foothold into a corporate cloud infrastructure from the outside world.*

### Primary Attack Vectors
*   **Exposed Secrets & Credential Leaks**: Scanning open-source repositories (GitHub, GitLab) and public code leaks for hardcoded AWS Access Keys, Azure Service Principal secrets, or GCP service account private keys.
*   **Server-Side Request Forgery (SSRF)**: Exploiting classic web app vulnerabilities (your existing baseline) to force a cloud-hosted virtual machine to call its internal **Instance Metadata Service (IMDS)** address (`http://169.254.169.254`) and extract temporary security credentials.
*   **Public S3/Storage Bucket Exposure**: Enumerating misconfigured, unauthenticated cloud storage objects containing sensitive corporate backups, code repositories, or configuration maps.

### Tooling to Master
*   **TruffleHog / GitLeaks**: High-utility automated tools for scanning commits, branches, and code history for leaked API keys.
*   **Pacu**: The premier, modular open-source AWS exploitation framework designed by Rhino Security Labs.
*   **Microburst**: A collection of powerful PowerShell scripts specifically designed for enumerating and attacking Azure services.

---

## 📈 Phase 3: Cloud Privilege Escalation & Lateral Movement
*Once you have landed inside a low-privilege cloud container or role, your next objective is to manipulate configurations to achieve Cloud Admin/Global Root authority.*

### Key Privilege Escalation Vectors
*   **IAM Policy Abuse (AWS)**: Finding overly permissive administrative parameters on a role you control (e.g., `iam:CreatePolicyVersion`, `iam:AttachUserPolicy`, `sts:AssumeRole`) to upgrade your own permissions.
*   **App Registrations (Azure/Entra ID)**: Finding a compromised application inside an Azure tenant that has high-privilege permissions assigned to it, allowing you to generate a new secret and hijack its access tokens.
*   **Service Account Over-Privilege (GCP)**: Actively attaching a high-privilege service account to a low-privilege virtual machine instance to hijack its execution identity.

### Lateral Movement & Pivoting
*   **Cloud-to-On-Premise (and vice versa)**: Exploiting hybrid integrations. Abusing Azure Entra Connect to pull hashes from an on-premise active directory domain controller, or using an on-premise footprint to access cloud configuration profiles.

### Best Free Training Platforms & Labs
*   **CloudGoat**: A free, deployable "vulnerable-by-design" AWS infrastructure framework by Rhino Security Labs. Run it directly within the AWS Free Tier to practice automated IAM privilege escalation scripts.
*   **IAM Vulnerable**: An open-source tool used to spin up vulnerable-by-design AWS IAM privileges to test exploitation paths.

---

## 📦 Phase 4: Container & Kubernetes (K8s) Defacement
*Modern enterprise cloud infrastructures rely heavily on containerized architectures. You must learn how to break out of single application containers into the host environment.*

### Core Concepts to Master
*   **Container Architecture**: Dockerfile layers, container namespaces, cgroups, and mounting properties.
*   **Kubernetes Components**: Pods, Nodes, Kubelet API, etcd database, and Service Accounts.

### Primary Attack Vectors
*   **Container Escape**: Exploiting container runtimes or abusing privileged flag configurations (`--privileged`) to execute root commands directly on the underlying cloud host operating system.
*   **K8s Service Account Token Theft**: Extracting cleartext JWT tokens automatically mounted inside vulnerable pods (`/var/run/secrets/kubernetes.io/serviceaccount/token`) to authenticate against the primary API server.

### Best Free Training Platforms & Labs
*   **Kubernetes Goat**: An open-source, free, highly practical interactive lab blueprint designed to teach you how to audit and exploit real-world Kubernetes security flaws.

---

## 🥷 Phase 5: Cloud C2, Persistence, & Defense Evasion
*Red teamers must remain invisible. Learn how to maintain your cloud presence without alerting corporate Security Operations Centers (SOCs).*

### Persistence Mechanisms
*   **Shadow Admin Accounts**: Creating backend secondary API access keys or secondary administrators on overlooked cloud user accounts.
*   **Malicious Automation Triggers**: Injecting malicious functions directly into serverless compute layers (AWS Lambda, Azure Functions) that run automatically when specific cloud objects are modified.

### Defense Evasion (Bypassing Logs)
*   **Disabling Logging Chains**: Executing commands to selectively stop or delete logging pipelines (e.g., `cloudtrail:StopLogging` or deleting S3 log storage policies).
*   **Log Alteration & Noise**: Generating thousands of benign API calls across diverse geolocations to blend your malicious operational commands into standard corporate noise.

### Tooling & Frameworks to Learn
*   **Skyline**: An open-source post-exploitation toolkit designed specifically for modern cloud operational tasks.
*   **Leonidas**: A framework used to automatically test detection system response times against specific cloud-attacker tactics.

---

## 📋 Actionable Checklist to Launch Your Cloud Red Team Track

- [ ] **Step 1:** Create an **AWS Free Tier Account** and a **Microsoft Azure Free Account**.
- [ ] **Step 2:** Use **TruffleHog** to search for public credential leaks across old open-source code repositories to understand how secrets leak.
- [ ] **Step 3:** Deploy **CloudGoat** on your AWS Free Tier infrastructure and manually run through the *iam_privesc_by_rollback* scenario.
- [ ] **Step 4:** Clone **Kubernetes Goat** locally onto your laptop and complete the first 3 container escape labs.
- [ ] **Step 5:** Read through **HackTricks (Cloud Section)** weekly to catalog real-world API call execution strings across AWS, Azure, and GCP.
