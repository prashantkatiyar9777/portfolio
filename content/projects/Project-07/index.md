---
title: "PRD for User Addition at Zenskar"
date: "2024-02-03"
slug: PRD for User Addition at Zenskar
category: projects
summary:
description:
cover:
  image: "Zenskar Cover.png"
  alt: "Zenskar Web Platform"
  caption: "Zenskar Web Platform"
  relative: false
showtoc: true
draft: false
---


### Introduction

This PRD specifies the requirements for the User Addition Feature within Zenskar's User Access Management Dashboard. Zenskar Dashboard, enabling hierarchical user addition and access assignment by SuperAdmins and Admins.

For a comprehensive understanding of Zenskar and its Access Management Dashboard, refer to the detailed overview:

<div class="notion-divider"></div>

**Purpose**

- **Add Users:** Enable the Super Admin and Admins to add new users to the Zenskar platform.
- **Assign Role and Access**: Assign specific roles and access rights to new users, ensuring they have the necessary permissions to perform their tasks.

<div class="notion-divider"></div>

### Functional Specifications (User Addition Workflow)

<div class="notion-style-box">
1️⃣ Permissions Matrix
    <br/><br/>
    The following table outlines the capabilities of each role in the user addition process:
    <aside>

1. Users Hierarchy
    
    ![Hierarchy Tree](Tree.png)
    <p style="text-align: center; margin-top: 5px; font-size:15px;">Super-Admin > Admin > Normal Users</p>
    
2. Super Admin Role
    - **Creation**: The account which purchased the subscription is Super Admin.
    - **Permissions**: Full user management and billing access.
3. Admin Role
    - **Creation**: Super-Admin can only assign Admin roles to users.
    - **Permissions**: Access to create, modify or delete a team in the respective domain.
4. Regular User Role
    - **Creation**: Created by respective Admins.
    - **Permissions**:  Access to assigned application features only.
    </aside>
</div>

<div class="notion-style-box">
2️⃣ User Account Management
    <aside>

1. Creating User Accounts
    - **Fields**: Name, Organisation’s Email, Secondary Email, Domain (Sales / Finance / Tech), Role (User / Admin / SuperAdmin)
    - **Validation**: Organisation’s Email: only company’s domain. Secondary Email: Only @icloud.com, @gmail.com, or @outlook.com to avoid fake temporary emails.
    - **Email Format**: Use Regex [^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$].
2. Modifying User Accounts
    - **Allow edits**: Name, Role, Department.
    - **Restrictions**: Secondary Email is non-editable.
3. Deleting User Accounts
    - **Process**: Soft delete with a 30-day recovery period,
    - **Permissions**: Only Admins and Super Admin.
    </aside>
</div>

<div class="notion-style-box">
3️⃣ New User Invitation Process
    <aside>

1. Inviting New Users
    - **Functionality**: Admins and Super Admins can invite new users.
    - **Method**: Invitations will be sent via email containing a unique link.
    - **Expiry Period**: The invitation link will have an expiry period of 72 hours.
2. Account Creation for Invitees:
    - **Requirement**: Invitees must create a Zenskar account to accept an invitation.
    - **Process**: On clicking the invitation link, non-registered users will be redirected to the account creation page.
3. Dashboard Feature for Invitations
    - **Implementation**: A tab to be made in the dashboards of Super Admins and Admins to add and invite new users.
    - **Functionality**: It will allow them to manage invitations, track pending invitations, and view the history of sent invitations.
    </aside>
</div>

<div class="notion-style-box">
4️⃣ Access Rights and Permissions
    <aside>

1. Assigning Roles
    - **Process**: Default to 'user'; Super Admin elevates roles from a predefined list to promote them to admin or demote.
2. Assigning Domain/Department
    - **Process**: SuperAdmin can set at creation. Users will inherit their creator Domain.
3. Managing Permissions
    - **Super Admins:** Have all the permissions.
    - **Admins and Users:** Defined per domain:
        >
        | Role | Domain Access |
        | --- | --- |
        | Sales | Access to Contract Builder, Customer Data, CRM Integration |
        | Tech | Access to Usage Data, Integration APIs |
        | Finance | Access to Invoice Builder, Payments Board, Payment Reminders |
    - **User Interface**: Super Admins get a dedicated dashboard to create users, assign admin roles and see audit and compliance reports. Admins get a similar dashboard but are limited to respective team building and reports.
4. Revoking Access
    - **Immediate Effect**: Access is revoked in real-time and logged with timestamps.
    - **Revoking Hierarchy**: Super-Admin **>** Admin **>** Normal User.
    </aside>
</div>

<div class="notion-style-box">
5️⃣ Testing Strategy
    <aside>

1. **Unit Testing:** Ensure individual components meet functional requirements.
2. **Integration Testing:** Validate interactions between different parts of the UAM feature.
3. **User Acceptance Testing:** Conduct tests with target user groups to confirm usability and effectiveness.
    </aside>
</div>

<div class="notion-style-box">
6️⃣ Audit and Compliance
    <aside>

1. User Activity Logs
    - **Contents**: Login attempts, changes made, timestamps. (Logs should record who made the change, when, and what the change was).
    - **Access**: Respective Admins and Super Admin.
2. Monthly Compliance Reports detailing user list, role changes, and access revocations.
    </aside>
</div>

<div class="notion-style-box">
7️⃣ Use Cases
    <aside>

1. **Super Admin Onboarding**: A super admin sets up their organisation's structure in Zenskar, defining roles and permissions.
2. **Role Modification**: An admin modifies user roles to reflect changes in the team structure.
    </aside>
</div>

<div class="notion-style-box">
8️⃣ Technical Requirements
    <aside>

1. To define specific API endpoints for user management functions.
2. To outline data storage needs for user information and logs.
    </aside>
</div>

<div class="notion-divider"></div>

<div class="notion-style-box">
📌 Non-Functional Specifications
    <aside>

1. Security: 
    - **At Rest**: AES-256 encryption.
    - **In Transit**: TLS 1.3.
    - **Authentication Method**: OAuth 2.0, Multi-Factor Authentication (MFA)
2. Performance: 
    - Response times ≤ 2 seconds for user actions
    - ≤ 5 seconds for system actions, scalable up to 10,000 users.
3. Reliability: Target 99.9% uptime daily backups.
4. Compliance: 
    - GDPR Data Protection Regulation.
    - ISO 27001 Compliance Auditing Standard
    </aside>
</div>

<div class="notion-divider"></div>

## Conclusion

This PRD provides a comprehensive specification for the UAM feature in Zenskar, aiming to deliver clear, precise requirements to the development team and facilitate a development process without the need for assumptions.

<div class="notion-divider"></div>

# Full-text article
[Read article](https://kprashant.notion.site/kprashant/Humantic-AI-PRD-Prashant-Katiyar-6cd9f325db6441f5aa95fa6e21032fb5)