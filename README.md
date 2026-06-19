Enterprise Active Directory & Group Policy Security Home Lab

An enterprise-grade Active Directory Domain Services (AD DS) and Group Policy (GPO) sandbox engineered inside a virtual Windows Server 2022 environment. This project demonstrates centralized identity management, organizational unit (OU) engineering, strict security baseline enforcement, and system-level troubleshooting.

🛠️ Core Administrative & Engineering Skills Demonstrated

Directory Services Architecture: Multi-layered OU design, structural protection (accidental deletion locks), and global/nested group structures.

Security & Baseline Management: GPO targeting, policy precedence modeling, workstation lockdown (Control Panel prohibition), and desktop environment standardization.

Enterprise Diagnostics & Triage: Resultant Set of Policy (RSOP) analysis, command-line Active Directory validation, and database relationship troubleshooting.

🏗️ Lab Architecture Overview

               🏢 [Windows Server 2022 Domain Controller]
                                │
               📁 [OU: Global Marketing (Parent Container)]
                                │
         ┌─────────────────────┼─────────────────────┐
         ▼                     ▼                     ▼
📁 [Digital Campaigns]  📁 [Content Creation] 📁 [Market Research]
   ├── 👤 arivera          ├── 👤 jtaylor        ├── 👤 cmorgan
   └── 👥 g-Digital        └── 👥 g-Content      └── 👥 g-Research


📁 Repository Directory Structure

To easily review the deployment steps, diagnostic logs, and physical configurations, navigate through the directory paths below:

📄 README.md: Main landing page and high-level architectural overview.

📁 documentation/: Completed technical walkthroughs and change logs.

📄 Day 1: Enterprise OU & Security Groups Setup: Building directory boundaries, safety structures, and validating database user links via terminal.

📄 Day 2: GPO Lockdowns & Simulation Validation: Hardening user access, enforcing visual baselines, and simulating logons using the DC engine.

📁 screenshots/: Visual confirmation, command output logs, and simulation report summaries.

🚨 Highlighted Troubleshooting Triage (Recruiter Highlights)

Hiring managers need system administrators who know what to do when configurations fail. These real-world scenarios from the lab build highlight my diagnostic processes:

1. The Active Directory "Missing Link" Issue

The Scenario: Upon initial setup, a command-line net user /domain query revealed a newly provisioned user account was missing its associated department global security group membership token.

The Diagnostic & Resolution: Inspected the graphical Active Directory database properties tab, identified that the logical relationship link had not been committed during creation, manually reassigned and applied the group membership, and re-validated using CLI.

Read the full case study in the Day 1 Report.

2. GPO Verification Without Dedicated Client Hardware

The Scenario: Lacked local Windows client client virtual machines to physically boot and execute local GPO checks (gpresult /r) to test Control Panel and wallpaper restrictions.

The Diagnostic & Resolution: Pivoted to logical virtualization modeling. Launched the Group Policy Modeling engine in gpmc.msc, targeted user arivera, and simulated the logon against the local Domain Controller object to verify the Resultant Set of Policy (RSOP) calculations directly on the database.

Read the full case study in the Day 2 Report.

🚀 How to Replicate This Lab Environment

For system administrators or fellow students looking to replicate this environment from scratch:

Review the step-by-step Day 1 Guide to build your OU containers, security groups, and users.

Go through the Day 2 Guide to build and link GPO restrictions.

If your workspace gets messy, run the Clean Teardown Procedures to keep your Active Directory database clean and prevent orphaned links.