This project is a hands-on Azure security lab built to show more than basic deployment skills. The goal is to design a small but realistic cloud environment that is secure by default, observable under attack, and easy to control from a cost and lifecycle perspective.
The lab is based on a simple two-tier scenario. A frontend virtual machine is exposed to the internet and acts as the only public entry point. A backend virtual machine sits behind it in a separate subnet, with no public IP and no direct internet access. Communication is intentionally limited so that traffic follows a clear path: external users can reach the frontend, and the frontend can reach the backend when needed, but the backend cannot be contacted directly from outside the environment.
The point of the project is not just to “make Azure resources work.” It is to demonstrate the kind of thinking expected in a security-focused cloud role:

reducing exposure,
applying least privilege,
centralizing logs,
detecting suspicious activity,
and cleaning up resources responsibly.

This makes the project interview-friendly because every technical choice has a reason behind it. The subnet separation is there to reduce blast radius. The backend has no public access because internal systems should not be exposed without necessity. Logging is centralized because security controls are only useful if activity can be observed, investigated, and acted on. Monitoring and alerts are included because prevention alone is not enough in a real environment.
The final deliverable is a GitHub project that documents the environment end to end. It includes the architecture, deployment choices, security controls, monitoring configuration, attack simulation results, and cleanup automation. The goal is to present a project that feels like a small security engineering case study rather than a collection of screenshots.
By the end, this lab should show that I can:

build and secure Azure infrastructure,
justify security decisions clearly,
verify that controls work through testing,
and manage the environment in a way that is practical, cost-aware, and production-minded.
