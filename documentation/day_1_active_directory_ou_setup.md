Lab: Building Enterprise Active Directory Architectures & Group Provisioning

🎯 Project Objective

The objective of this hands-on lab is to design, implement, and validate an enterprise-grade Active Directory Domain Services (AD DS) organizational structure on Windows Server 2022. This environment establishes robust security administrative boundaries, enforces structural protection to prevent catastrophic accidental deletions, and maps functional department users to distinct security groups to enable scalable network resource access control.

🛠️ Technologies & Tools Used

Operating System: Windows Server 2022 (Domain Controller)

Directory Services: Active Directory Domain Services (AD DS)

Management Tools: Remote Server Administration Tools (RSAT), Active Directory Users and Computers (ADUC) console

Command Line Tools: Command Prompt (net user), PowerShell (Get-ADUser)

🏗️ Architecture & Configuration Steps

Step 1: Organizational Unit (OU) & Security Group Provisioning

Configured a parent Organizational Unit (OU) named Global Marketing to serve as the administrative boundary.

Provisioned three nested departmental sub-OUs: Digital Campaigns, Content Creation, and Market Research to isolate department-specific resources.

Accidental Deletion Protection: Enabled "Protect container from accidental deletion" across all OUs. In a production network, this prevents administrative mishaps from dismantling critical directory structures.

Step 2: User Creation & Directory Structuring

Created three corporate user accounts with standard naming conventions matching administrative policies:

arivera (Digital Campaigns)

jtaylor (Content Creation)

cmorgan (Market Research)

Provisioned matching global Security Groups for department mapping (e.g., g-Marketing-DigitalCampaigns).

🚨 Real-World Troubleshooting & Diagnostics (Crucial for Recruiters!)

Hiring managers value engineers who can diagnose failures under pressure. During the validation phase of this build, a synchronization and database linking issue occurred.

The Issue: Failed Database Group Verification

Symptom: Running the command-line verification net user arivera /domain inside the terminal returned only the default *Domain Users membership. The custom department security group *g-Marketing-DigitalCampaigns was completely missing from the user’s token.

Diagnostic Action: Opened the ADUC console, checked the properties of the user arivera, and inspected the Member Of tab. Verified that the physical object was located in the correct OU but lacked the logical database link.

Root Cause: The database relationship link between the user account and the security group object had not been committed or applied successfully during the initial creation phase in the graphical interface.

Resolution: Manually reassigned the group link under the user properties tab, clicked Apply to write the configuration to the Active Directory database, and successfully reran the command-line validation.

📊 Verification & Validation (Proof It Works)

To verify the integrity of the Active Directory database, the configuration was checked using native command-line diagnostic tools.

net user arivera /domain


Validation Output

The terminal output confirms that the user arivera is now successfully associated with both the default domain group and the nested department group:

Global Group memberships     *Domain Users    *g-Marketing-DigitalCampaigns
The command completed successfully.


Verification complete: Logical database links are fully operational and active across the domain controller.