# azure-secure-lab-rg


Project Definition
Goal: Build a secure, monitored Azure lab environment with lifecycle/cost control.
Scenario: Internet-facing frontend VM, isolated backend VM, controlled access, logging, and attack detection.
Output: A GitHub project that demonstrates architecture, security reasoning, monitoring, and automation.
Environment Setup
Create one resource group: azure-secure-lab-rg
Region: choose one and keep consistent
Naming convention:
vnet-secure-lab
subnet-frontend / subnet-backend
vm-frontend / vm-backend
Use Microsoft Azure portal or CLI
Network Architecture
Create VNet: 10.0.0.0/16
Subnets:
frontend: 10.0.1.0/24
backend: 10.0.2.0/24
Design rules:
frontend = exposed layer
backend = isolated layer
No public IP on backend VM
Define clear traffic flow:
Internet → frontend
frontend → backend
Internet → backend = blocked
Virtual Machines Deployment
Frontend VM:
Public IP
Install web server (nginx/apache)
SSH key-based authentication only
Backend VM:
No public IP
Accessible only from frontend subnet
Minimal services running
Network Security Configuration
Create NSG for frontend subnet:
Allow HTTP (80) from Any
Allow SSH (22) from your IP only
Deny all other inbound
Create NSG for backend subnet:
Allow SSH (22) from frontend subnet only
Deny all inbound from Internet
Apply “deny by default” logic using Azure Network Security Group
System Hardening
Disable password-based SSH
Restrict SSH access (IP filtering)
Ensure OS updates are applied
Close unnecessary ports
Keep configuration minimal and justified
Logging and Monitoring
Create a Log Analytics workspace using Azure Log Analytics
Enable:
NSG flow logs
VM logs (syslog/auth)
Use Azure Monitor to:
centralize logs
query activity
Detection Rules (KQL)
Implement queries:
Detect port scanning (high number of connections)
Detect denied traffic
Detect failed SSH attempts
Store queries in project files
Validate they return real data
Alerting
Create at least one alert rule:
Example: high number of denied connections
Trigger action:
email notification
Ensure alert actually fires during testing
Attack Simulation
Simulate external scan:
use nmap on frontend public IP
Attempt unauthorized access:
SSH directly to backend (must fail)
Optional:
brute-force simulation (controlled)
Validate:
logs are generated
alerts triggered
traffic blocked correctly
Cost Control / Lifecycle Management
Place ALL resources in one resource group
Implement scripts:
Script 1:
Stop and deallocate all VMs
Script 2:
Delete entire resource group
Script 3 (optional but strong):
List leftover resources (disks, IPs)
Use tagging:
Environment=Lab
AutoDelete=Date
Base logic on Azure Resource Manager
Repository Structure
Create folders:
architecture/
infrastructure/
security/
monitoring/
attack-simulation/
cost-control/
screenshots/
Keep files clean and readable
Separate code, explanation, and results
Architecture Diagram
Use draw.io
Include:
VNet
subnets
VMs
NSG
traffic arrows
Keep it simple and readable
Screenshots
Limit to 4–6 images:
architecture
NSG rules
logs/query results
alert trigger
Each screenshot must include explanation
README Documentation
Structure:
Objective
Architecture overview
Services used
Network design
Security controls
Monitoring & detection
Attack simulation
Results
Cost control
What you learned
Limitations
Improvements
Focus on explaining “why”, not just “what”
Security Reasoning (critical)
Be able to explain:
Why subnet separation exists
Why backend has no public access
Why least privilege is applied
Why logging is centralized
Why detection is necessary
Validation
Before publishing:
All components deployed and working
Attack scenarios produce logs
Alerts trigger correctly
Scripts work without errors
README is clear and structured
Optional Enhancements (only if time allows)
Add Azure Sentinel
Use Infrastructure as Code (Bicep/Terraform)
Add Just-In-Time VM access
Improve alerting logic
Final Outcome
You should end up with:
A functional secure cloud environment
Real monitoring and detection
A lifecycle/cost control system
A project you can explain end-to-end in an interview
Execution Strategy
Week 1:
Build infrastructure + security
Week 2:
Logging, detection, attack simulation
Documentation + cleanup scripts
Goal:
Not just “working project”
But fully explainable engineering work
