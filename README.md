# 🔐 Microsoft Entra ID — Identity Governance & Access Reviews Lab
### Access Certification • Guest Lifecycle Control • Least Privilege Enforcement

<img width="1536" height="1024" alt="3285c511-f0e0-43d4-9557-169b0f0aa54f" src="https://github.com/user-attachments/assets/f909bae8-2b7d-434d-89e0-06d3c3997fed" />

**Author:** Felipe Restrepo  
**Category:** Identity & Access Management (IAM) / Identity Governance  
**Platform:** Microsoft Entra ID (Azure AD)  
**Core Features:** Groups, Users, Guest Access, Identity Governance, Access Reviews, Audit Logs

---

## 📘 Project Overview

This project documents a hands-on **Identity Governance** lab in **Microsoft Entra ID** focused on **access certification** and **third-party (guest) access control**.

The lab simulates a real enterprise scenario where contractor access must be reviewed and removed if no longer needed. It includes:

- Enterprise security group model
- Cloud-only users assigned to departments
- Guest user invited as a contractor
- Access Review configured for the contractor group
- Governance evidence captured via Entra audit logs

---

## 🎯 Objectives

- Build an enterprise group model for department access
- Create cloud-only users and assign them using RBAC-style groups
- Invite an external guest user for contractor access
- Configure an Access Review for the contractor group
- Record access certification decisions (approve/deny)
- Validate governance activity with Entra audit logs

---

## 🧱 Environment

- **Directory:** Microsoft Entra ID Tenant
- **Groups:** Security groups (Assigned membership)
- **Users:** Cloud-only users + Guest user
- **Governance:** Identity Governance → Access Reviews
- **Evidence:** Audit Logs + Group membership validation

---

## 🏗 Architecture (High-Level)

Microsoft Entra ID Tenant  
→ Security Groups (HR / IT / Finance / Contractors)  
→ Users assigned to department groups  
→ Guest added to Contractors group  
→ Access Review certifies contractor access  
→ Audit logs record governance events

---

## ✅ Implementation Steps (Step-by-Step)

---

## 🔹 PHASE 1 — Environment Setup

### Step 1 — Create Enterprise Security Groups

**Path:** Azure Portal → Microsoft Entra ID → **Groups** → **New group**

Create the following groups:

- **ENT-HR-Users**
- **ENT-IT-Admins**
- **ENT-Finance-Users**
- **ENT-Contractors**

**Settings:**
- **Group type:** Security  
- **Membership type:** Assigned  

📸 **Screenshot Evidence:**  

<img width="673" height="201" alt="1" src="https://github.com/user-attachments/assets/c513b035-1669-4445-8e48-cc4f799e8554" />

<img width="1349" height="601" alt="2" src="https://github.com/user-attachments/assets/943205df-e54a-4a0d-8ace-dbe8b4217b6e" />

---


### Step 2 — Create Cloud-Only Users + Assign Groups

**Path:** Microsoft Entra ID → **Users** → **New user**

Create at least:

- `alex.hr`
- `maria.finance`
- `kevin.it`

Assign each user to the correct group:

- `alex.hr` → **ENT-HR-Users**
- `maria.finance` → **ENT-Finance-Users**
- `kevin.it` → **ENT-IT-Admins** (or IT user group if you prefer)

📸 **Screenshot Evidence:**  

<img width="866" height="243" alt="3" src="https://github.com/user-attachments/assets/debd9d9f-47fc-414e-9a67-e01760a1e303" />

<img width="1357" height="597" alt="4" src="https://github.com/user-attachments/assets/9f7e6481-ccb2-42ef-8c3c-2ee93d18be9a" />

<img width="971" height="458" alt="5" src="https://github.com/user-attachments/assets/9128182a-e4f9-42f8-8af5-704d1b1ff4ce" />

<img width="1358" height="603" alt="6" src="https://github.com/user-attachments/assets/9adde29c-dc23-4fae-a9c5-438bd3a1b7e2" />

<img width="1356" height="603" alt="7" src="https://github.com/user-attachments/assets/b796dba2-6f30-4bb1-b87b-38e153016feb" />

---

## 🔹 PHASE 2 — Guest + Risk Scenario

### Step 3 — Invite a Guest User (Contractor)

**Path:** Microsoft Entra ID → **Users** → **New user** → **Invite external user**

- Invite a guest using one of your emails
- Add the guest user to: **ENT-Contractors**

**Purpose:** Simulates **vendor / third-party access**.

📸 **Screenshot Evidence:**  

<img width="877" height="357" alt="8" src="https://github.com/user-attachments/assets/0077a527-1ed1-4f45-aba0-b7bc4d3acd67" />

<img width="1088" height="575" alt="9" src="https://github.com/user-attachments/assets/c31c2cf0-18cc-4f01-bc00-f67648381d93" />

<img width="1085" height="556" alt="10" src="https://github.com/user-attachments/assets/fd4d193c-9c30-4704-9e63-efd5b2aaa51e" />

<img width="1359" height="169" alt="11" src="https://github.com/user-attachments/assets/473105b8-1253-4a8e-999e-cf7762b5d825" />

<img width="1104" height="578" alt="12" src="https://github.com/user-attachments/assets/cd30a204-d371-467a-9e70-b8c6b88fdf95" />

---

## 🔹 PHASE 3 — Identity Governance (Core Skill)

### Step 4 — Create an Access Review (Access Certification)

**Path:** Microsoft Entra ID → **Identity Governance** → **Access Reviews** → **New**

**Configuration:**
- **Review type:** Teams + Groups  
- **Select group:** **ENT-Contractors**  
- **Reviewers:** Group owners  
- **Frequency:** One time  
- **Duration:** 3 days  
- **On completion:**  
  - ✅ Auto-remove denied users  
  - ✅ Auto-apply results  

📸 **Screenshot Evidence:**  

<img width="913" height="554" alt="14" src="https://github.com/user-attachments/assets/53a6c45a-fbce-4340-9a95-649d02d3b997" />

<img width="1089" height="555" alt="15" src="https://github.com/user-attachments/assets/6bae78ce-a2e0-4cd5-bb9d-57f7bc03197d" />

<img width="1068" height="552" alt="16" src="https://github.com/user-attachments/assets/df08ea18-00a9-4f48-8c9a-ccf8a44f1590" />

---

### Step 5 — Start Review + Record Decision

**Path:** Identity Governance → Access Reviews → Open the review → **Results**

- Review the guest user in scope
- **Approve** or **Deny** access (based on your scenario)
- Capture evidence of the recorded decision

📸 **Screenshot Evidence:**  

<img width="1090" height="574" alt="17" src="https://github.com/user-attachments/assets/468855c2-7621-4d19-8607-fee0a8bb9e0a" />

<img width="1093" height="567" alt="18" src="https://github.com/user-attachments/assets/b56fb7cc-045d-498c-9d80-6fee26b7a6a7" />

<img width="1091" height="569" alt="19" src="https://github.com/user-attachments/assets/db027b61-c953-4537-a890-51f4d9be2f11" />

> Note: Depending on configuration, “Stop” may be unavailable while the review is within the scheduled review period. In that case, enforcement occurs automatically at review completion.

---

## 🔹 PHASE 4 — Evidence & Validation

### Step 6 — Confirm Membership Change (Removal or Retention)

**Path:** Microsoft Entra ID → **Groups** → **ENT-Contractors** → **Members**

Confirm whether the guest was:

- ✅ Removed (if denied + applied)  
or  
- ✅ Maintained (if approved or review not yet enforced)

📸 **Screenshot Evidence:**  

<img width="969" height="564" alt="Screenshot 2026-01-17 123453" src="https://github.com/user-attachments/assets/d13a20cc-247a-4874-8948-fc97ffaec4af" />

---

### Step 7 — Capture Governance Audit Logs

**Path:** Microsoft Entra ID → **Monitoring** → **Audit logs**

Filter:
- **Category:** Identity Governance

Look for events related to:
- Access Review creation
- Access Review decision recorded
- Result application / membership change (if applicable)

📸 **Screenshot Evidence:**  

<img width="1360" height="599" alt="20" src="https://github.com/user-attachments/assets/5b23ed6a-a9b9-46c2-9d7a-8a9b1cf1cb99" />

<img width="852" height="562" alt="21" src="https://github.com/user-attachments/assets/8c3ebdc2-c49e-4497-a68b-71f0e0c481bc" />

---

## 🔍 Skills Demonstrated

- Enterprise security group design (RBAC-style group model)
- Cloud-only user provisioning and access assignment
- Guest/contractor onboarding and access control
- Identity Governance Access Reviews (access certification)
- Governance evidence collection using Entra audit logs
- Least privilege enforcement through access review outcomes

---

## 📌 Key Takeaways

- Access Reviews help organizations reduce stale or unnecessary access
- Guest access should be periodically certified to manage third-party risk
- Identity Governance provides audit-ready evidence of access decisions
- Group-based access models scale better than direct user assignments
