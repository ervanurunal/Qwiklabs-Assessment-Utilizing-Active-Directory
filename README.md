## Utilizing Active Directory on Windows

---

### Overview

In this lab, I worked with **Active Directory**, a centralized system used to manage Windows users, groups, machines, and policies. I installed and configured Active Directory, created users and groups, managed group memberships, and created a Group Policy Object (GPO).

The lab provided hands-on practice with centralized Windows administration and access management.

---

### Tools & Resources

* Windows Virtual Machine
* Windows PowerShell
* Active Directory Domain Services (AD DS)
* Active Directory Administrative Center (ADAC)
* Group Policy Management
* Group Policy Management Editor
* Windows Server
* Active Directory Users and Groups
* Group Policy Objects (GPOs)


### Lab Type: 
Windows / Active Directory / System Administration Hands-On Lab

---
---

## 1. Install Active Directory

Open **Windows PowerShell as Administrator**.

![1](https://i.imgur.com/2mxhYxq.png)

The lab provides a PowerShell command to install Active Directory Domain Services.

```powershell
C:\Qwiklabs\ADSetup\active_directory_install.ps1
```

![2](https://i.imgur.com/6nYRhZK.png)

The installation may take several minutes and automatically restarts the computer when completed.

After the restart, reconnect to the Windows VM.

![3](https://i.imgur.com/rtoRRW2.jpeg)

![4](https://i.imgur.com/XidHdiZ.png)

---

## 2. Open Active Directory Administrative Center

Open the **Active Directory Administrative Center (ADAC)**.

From the Windows Start menu, search for:

```text
active
```

Then open:

```text
Active Directory Administrative Center
```

![5](https://i.imgur.com/eKxtMzg.png)

ADAC allows administrators to manage:

* Users
* Groups
* Computers
* Active Directory resources

---

## 3. Create a New User

Navigate to:

```text
example (local) → Users
```

Select:

```text
New → User
```

![6](https://i.imgur.com/5ItwGj0.png)

Create the following user:

| Field    | Value |
| -------- | ----- |
| Name     | Alex  |
| Username | alex  |

Only the required fields need to be completed.

![7](https://i.imgur.com/PsS9e0I.png)

---

## 4. Enable the User Account

After creating Alex, the account initially appears as:

```text
Alex (Disabled)
```

![8](https://i.imgur.com/xiXlt2C.png)

Attempting to enable the account without a password produces an error because the password does not meet the domain requirements.

The lab demonstrates that an account requires an acceptable password before it can be enabled.

---

## 5. Reset the User Password

Select the user and choose:

```text
Reset Password
```

![8](https://i.imgur.com/ugqm98q.png)

Set a password that satisfies the domain requirements.

Keep the following option enabled:

```text
User must change password at next logon
```

This requires the user to create their own password when they first log in.

After setting the password, enable the Alex account.

![9](https://i.imgur.com/DWUWr6A.png)

---

## 6. Create a New Group

Navigate to the Users section and select:

```text
New → Group
```

![10](https://i.imgur.com/tN4rrKJ.png)

Create:

```text
Python Developers
```

The group name is the required information for this lab.

![11](https://i.imgur.com/RCRlM03.png)

---

## 7. Add Python Developers to Developers

Right-click:

```text
Python Developers
```

Select:

```text
Add to another group
```

![12](https://i.imgur.com/OWyGYPq.png)

Enter:

```text
Developers
```

![13](https://i.imgur.com/arGUvyb.png)

Use **Check Names** to verify the group name.

Then click **OK**.

This makes:

```text
Python Developers
        ↓
   Developers
```

---

## 8. Add Alex to Python Developers

Open:

```text
Python Developers
```

Navigate to the:

```text
Members
```

section.

Select **Add** and enter:

```text
Alex
```

![14](https://i.imgur.com/8u9RVCj.png)

Click **OK** to add the user.

The resulting relationship is:

```text
Alex
  ↓
Python Developers
  ↓
Developers
```

![15](https://i.imgur.com/5fdLb2Y.png)

---

## 9. Edit User Group Membership

The lab also includes an existing user named:

```text
Alosha
```

The goal is to move Alosha from:

```text
Java Developers
```

to:

```text
Python Developers
```

Open Alosha's properties and select:

```text
Member Of
```

Remove:

```text
Java Developers
```

![16](https://i.imgur.com/62J7DjH.png)

Then select **Add** and add:

```text
Python Developers
```

![17](https://i.imgur.com/OKGSh70.png)

---

## 10. Open Group Policy Management

Open the Windows Start menu and search for:

```text
group
```

Open:

```text
Group Policy Management
```

![18](https://i.imgur.com/fXvzHLH.png)

Group Policy allows administrators to configure how computers and users in a domain behave.

Policies can be applied to the entire domain or to specific **Organizational Units (OUs)**.

---

## 11. Create a New Group Policy Object

Navigate to:

```text
example.com
    └── Developers
```

![19](https://i.imgur.com/GCf80W7.png)

Right-click the **Developers** OU.

Select:

```text
Create a GPO in this domain, and Link it here
```

Name the policy:

```text
New Wallpaper
```

![20](https://i.imgur.com/CsC21Tw.png)

---

## 12. Edit the Group Policy

Right-click:

```text
New Wallpaper
```

Select:

```text
Edit
```

![21](https://i.imgur.com/X4serVx.png)

This opens the **Group Policy Management Editor**.

Navigate to:

```text
User Configuration
    → Policies
        → Administrative Templates
            → Desktop
                → Desktop
```

Select:

```text
Desktop Wallpaper
```

![22](https://i.imgur.com/tTTn01X.png)

---

## 13. Configure Desktop Wallpaper

Double-click:

```text
Desktop Wallpaper
```

Select:

```text
Enabled
```

For the wallpaper path, enter:

```text
C:\Qwiklabs\wallpaper.jpg
```

Then click **OK**.

![23](https://i.imgur.com/QDsG3B8.png)

---
---

## Active Directory & Cybersecurity Relevance

Active Directory is important in enterprise cybersecurity because it provides centralized management of identities, groups, computers, and policies.

This lab helped me practice concepts related to:

* Identity and access management
* User account administration
* Group-based access management
* Password requirements
* Group membership
* Centralized policy management
* Organizational Units
* Security policy enforcement

Managing users and groups correctly is especially important because group membership can determine what resources a user can access.

---
---

## Key Concepts

| Concept                 | Description                                           |
| ----------------------- | ----------------------------------------------------- |
| Active Directory        | Centralized Windows directory service                 |
| AD DS                   | Active Directory Domain Services                      |
| User                    | Individual account managed by Active Directory        |
| Group                   | Collection of users or other groups                   |
| Group Membership        | Defines which groups an account belongs to            |
| OU                      | Organizational Unit used to organize/manage objects   |
| GPO                     | Group Policy Object containing configuration settings |
| Group Policy            | Centralized configuration management                  |
| ADAC                    | Active Directory Administrative Center                |
| Group Policy Management | Tool for managing domain policies                     |

---
---

## Group Membership Structure

The lab created the following relationship:

```text
Developers
    │
    └── Python Developers
            │
            └── Alex
```

Alosha's membership was changed from:

```text
Alosha
   └── Java Developers
```

to:

```text
Alosha
   └── Python Developers
```

---
---

## Administrative Tools Used

### Active Directory Administrative Center

Used for:

* Creating users
* Creating groups
* Managing memberships
* Editing user properties
* Managing Active Directory objects

### Group Policy Management

Used for:

* Creating GPOs
* Linking GPOs to OUs
* Managing domain policies

### Group Policy Management Editor

Used for:

* Editing individual policy settings
* Configuring user and computer policies

---
---

## Troubleshooting Example

### Problem

The newly created **Alex** account could not be enabled.

### Error

```text
Failed to enable the account.
The password does not meet the length,
complexity, or history requirement of the domain.
```

### Cause

The account did not have a password that satisfied the domain's password requirements.

### Solution

1. Open **Reset Password**.
2. Set a compliant password.
3. Keep **User must change password at next logon** enabled.
4. Save the password.
5. Enable the account again.

---
---

## Skills Demonstrated

* Active Directory Administration
* Windows Server Administration
* User Account Management
* Group Management
* Group Membership Management
* Identity and Access Management
* Password Policy Awareness
* Organizational Units
* Group Policy Management
* Centralized Configuration
* Windows Troubleshooting

---
---

## Final Takeaway

This lab provided hands-on experience with **Active Directory administration**. I practiced creating and managing users and groups, modifying group memberships, and applying centralized configuration through Group Policy.

These are foundational Windows administration skills and provide practical experience with identity management, access control, and centralized security policy administration.
