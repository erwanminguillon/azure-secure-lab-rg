#Project Definition

#Why
The purpose of this project is to build a small Azure environment that demonstrates practical cloud security engineering, not just resource deployment. It is designed to show how to reduce exposure, separate trust boundaries, monitor activity, and respond to suspicious behavior in a way that is easy to explain in a technical interview. It also shows that security is not only about blocking access, but also about visibility, validation, and cost control.

#What
The project is a secure Azure lab built around a two-tier setup:

a frontend VM exposed to the internet,
a backend VM isolated from direct public access,
controlled communication between both layers,
centralized logging and monitoring,
basic threat detection and alerting,
lifecycle and cost-control scripts for cleanup and shutdown.

The final result is a GitHub project that documents the architecture, security decisions, monitoring setup, attack simulation, and operational controls.
#How
The lab is implemented by creating a single Azure environment with:

one resource group to keep all resources contained,
one virtual network with separate frontend and backend subnets,
a public-facing frontend VM and a private backend VM,
network security groups enforcing least-privilege traffic rules,
hardened VM access using SSH keys and limited inbound access,
Azure Monitor and Log Analytics for centralized logging,
KQL queries and alerts to detect suspicious activity,
controlled attack simulations to verify that security controls and logging work,
cleanup and shutdown scripts to manage cost and lifecycle.
