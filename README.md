# Secure Azure Lab
A small Azure security lab built to demonstrate practical cloud security engineering skills in a realistic setup.

# Overview
This project is designed to show how security decisions are applied in practice: reducing exposure, separating trust boundaries, monitoring activity, detecting suspicious behaviour, and keeping the environment manageable from both an operational and cost perspective.
The lab uses a simple two-tier architecture:

a frontend VM exposed to the internet,
a backend VM isolated from direct public access,
controlled communication between both layers,
centralised logging and monitoring,
basic threat detection and alerting,
cleanup and shutdown scripts for lifecycle and cost control.

The goal is to build a small but meaningful environment that demonstrates how cloud infrastructure can be deployed with security in mind from the start.

# Objectives
This project was built to demonstrate:

secure Azure network design,
least-privilege access control,
VM hardening basics,
centralised logging and monitoring,
detection of suspicious activity using KQL queries and alerts,
validation of controls through controlled attack simulation,
operational discipline through cleanup and cost-management scripts.


# Architecture
The environment is deployed inside a single Azure resource group and includes:

1 Resource Group to keep all resources contained
1 Virtual Network with separate subnets

Frontend subnet
Backend subnet


1 Public-facing frontend VM
1 Private backend VM
Network Security Groups (NSGs) enforcing restricted traffic rules
Azure Monitor + Log Analytics for centralised visibility
Alerting rules based on suspicious activity patterns
Lifecycle scripts for cleanup and shutdown


The frontend VM is the only system exposed externally. The backend VM is not directly reachable from the internet and only allows controlled communication from the frontend tier.

# Security Controls
This lab focuses on basic but important security engineering principles.
Network segmentation
The frontend and backend systems are placed in separate subnets to create clear trust boundaries.
Restricted inbound access
Only the minimum required inbound traffic is allowed. The frontend VM is exposed in a controlled way, while the backend VM has no public access.
Least-privilege NSG rules
Network Security Groups are used to limit communication paths and reduce unnecessary exposure.
Hardened VM access
Administrative access is restricted using SSH keys and tightly scoped inbound rules.
Centralised monitoring
Logs are collected in Azure Monitor and Log Analytics to improve visibility and support detection.
Detection and alerting
KQL queries and alert rules are used to identify suspicious behaviour and verify that monitoring is working as intended.

# Monitoring and Detection
To make the lab more than a static deployment, monitoring is treated as a core part of the design.
The environment includes:

centralised log collection,
Azure Monitor integration,
Log Analytics workspace queries,
basic detection logic using KQL,
alerting for suspicious or unexpected activity.

Examples of what this can help identify:

repeated failed authentication attempts,
unexpected network activity,
access from unusual sources,
other suspicious patterns generated during testing.

This part of the project is important because security is not only about prevention. It is also about visibility and being able to verify whether controls are actually effective.

Attack Simulation
To validate the setup, the lab includes controlled attack simulations.
These are used to test whether:

network restrictions behave as expected,
logging captures relevant activity,
detection queries return useful results,
alerts trigger when suspicious behaviour occurs.

The purpose is not to build an offensive lab, but to confirm that the defensive controls and monitoring pipeline are functioning correctly.

# Cost and Lifecycle Management
Because cloud environments can become expensive if left running, the project also includes basic operational controls.
This includes scripts for:

shutting down resources when not in use,
cleaning up the environment,
reducing unnecessary runtime costs,
keeping the lab easy to redeploy.

This helps show that security engineering also includes operational discipline, not just infrastructure deployment.

# Why I Built This
I built this project as a portfolio lab to demonstrate practical Azure security skills in a way that is easy to explain during interviews or technical discussions.
Rather than building a large environment, I focused on a small setup with clear security decisions and observable behaviour. The idea was to show not only what was deployed, but why it was deployed that way and how the controls were validated.

# Key Takeaways
This project demonstrates:

secure Azure infrastructure design,
segmentation between public and private workloads,
least-privilege access control,
monitoring and detection with Azure-native tools,
validation through controlled testing,
operational awareness around cost and cleanup.


# Possible Improvements
Future iterations could include:

Microsoft Defender for Cloud integration,
Just-in-Time VM access,
Azure Bastion for administrative access,
more advanced KQL detections,
automated deployment with Terraform or Bicep,
CI/CD integration for repeatable lab setup,
incident response playbooks.


# Repository Scope
This repository is intended to document:

the architecture,
the security decisions,
the monitoring setup,
the detection logic,
the validation process,
and the operational controls used to manage the lab.


# Notes
This is a personal learning and portfolio project built for demonstration purposes. The environment is intentionally small, but the design choices reflect real security engineering principles that can scale to larger Azure deployments.
