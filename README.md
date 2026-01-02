# IAM-Enterprise-Project
Hands-on Microsoft Entra IAM project demonstrating break-glass accounts, privileged access groups, conditional access, and MFA policies.

---

## **Project Overview**
This project demonstrates enterprise-level Identity and Access Management (IAM) using Microsoft Entra ID / Azure AD. It showcases the implementation of:

- Break-glass emergency accounts
- Privileged access groups
- Role-based access assignment following least privilege
- Conditional Access policies enforcing Multi-Factor Authentication (MFA)
- Audit logging and sign-in monitoring

---

## **Objectives**
1. Create break-glass accounts for emergency access.
2. Organize privileged users into groups and assign roles.
3. Implement Conditional Access with MFA for all privileged accounts.
4. Enable audit and sign-in logging to monitor activity.
5. Document configurations for transparency and review.

---

## **Break-Glass Accounts**
Two emergency accounts were created with the following properties:

| Username | Role | Cloud-only | Password Policy | Groups |
|----------|------|------------|----------------|--------|
| bg-admin-01@AcmeHealthServices.onmicrosoft.com | Global Administrator | Yes | 32+ characters, never expires | None |
| bg-admin-02@AcmeHealthServices.onmicrosoft.com | Global Administrator | Yes | 32+ characters, never expires | None |

📸 **Screenshot:** `Screenshots/break-glass-role.png`  

**Notes:**  
- These accounts bypass normal group-based access controls.  
- Used only for emergency access.

---

## **Privileged Access Groups & Roles**
Groups were created to enforce least-privilege access:

| Group Name          | Role Assigned         | Members                                         |
|--------------------|---------------------|------------------------------------------------|
| PrivilegedAdmins    | Global Administrator | it.admin, sec.admin                             |
| HelpDeskAdmins      | User Administrator   | helpdesk.user, hr.user                          |
| AppAdmins           | Application Admin    | dev.user, cloud.eng                             |

📸 **Screenshot:** `Screenshots/group-role-assignment.png`  

**Notes:**  
- Membership type is **Assigned**.  
- Break-glass accounts are **not included**.  
- This structure supports separation of duties and limits exposure of high-privilege roles.

---

## **Conditional Access + MFA**
Conditional Access policy was implemented to enforce MFA for all privileged users:

- Applied to groups: `PrivilegedAdmins`, `HelpDeskAdmins`, `AppAdmins`  
- Excludes break-glass accounts  
- Enforces MFA for all sign-ins to any cloud app  

📸 **Screenshot:** `Screenshots/conditional-access-mfa.png`  

**Notes:**  
- MFA ensures secure authentication for sensitive accounts.  
- Break-glass accounts remain accessible during emergencies without MFA prompts.

---

## **Audit Logging & Sign-in Monitoring**
Logging is enabled to monitor activity for all privileged users:

- **Audit Logs:** Track directory changes such as user creation, role assignments, and password resets.  
- **Sign-in Logs:** Record sign-ins by privileged accounts, including timestamp, location, device, and status.  

📸 **Screenshot:** `Screenshots/audit-logs.png`  

**Notes:**  
- Alerts for unusual sign-ins were recommended but not implemented in this version.  
- Logging ensures accountability and traceability of high-privilege actions.

---

## **Conclusion**
This project demonstrates real-world IAM security practices, including:

- Emergency access procedures using break-glass accounts  
- Least privilege principle through group-based role assignments  
- Conditional Access and MFA for privileged accounts  
- Logging and monitoring for visibility and accountability  

This setup is **resume-ready** and demonstrates hands-on skills for IAM and cybersecurity roles.

---

## **Screenshots Folder**
All screenshots referenced above are located in the `Screenshots/` folder:

Screenshots/  
├─ break-glass-role.png  
├─ group-role-assignment.png  
├─ conditional-access-mfa.png  
└─ audit-logs.png  


---

**Author:** Jaycob White  
**Organization:** Acme Health Services  
**Date:** January 2026
