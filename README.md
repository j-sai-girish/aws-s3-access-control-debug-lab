# AWS S3 Access Control & 403 Forbidden Debugging Lab (IAM vs Bucket Policy Conflict)

## 🧠 Overview
This project simulates a real AWS Cloud Support incident where an S3 object becomes inaccessible due to conflicting IAM and S3 Bucket Policy rules.

It demonstrates structured debugging of **403 Forbidden (AccessDenied)** errors in AWS S3.

---

## 🎯 Objectives
- Understand AWS S3 permission evaluation model  
- Compare IAM vs S3 Bucket Policies  
- Simulate real-world 403 Forbidden incident  
- Identify Explicit Deny precedence rule  
- Practice cloud troubleshooting workflow  

---

## 🏗️ Architecture
- S3 bucket hosts `index.html`
- IAM user (`s3-debug-user`) used for CLI access
- Bucket policy introduces Explicit Deny
- AWS CLI and Browser used for testing access

---

## 🛠️ Tools Used
- AWS S3  
- AWS IAM  
- AWS CLI  
- JSON Policy Editor  

---

## 🟢 Phase 1: Baseline Setup
- Created S3 bucket  
- Uploaded `index.html`  
- Created IAM user with `AmazonS3ReadOnlyAccess`  
- Verified CLI access successfully  

✔ System working before incident injection

---

## 💥 Phase 2: Incident Injection
An **Explicit Deny rule** was added in the S3 bucket policy to simulate a production security restriction.

This overrides IAM permissions intentionally.

---

## ❌ Phase 3: Incident (Failure State)
- Browser returns **403 AccessDenied**
- AWS CLI returns **403 Forbidden**

✔ Confirms access failure at S3 authorization layer

---

## 🕵️ Phase 4: Root Cause Analysis

### Investigation:
- IAM permissions verified (correct)
- Block Public Access ruled out
- Bucket policy inspected

### 🚨 Root Cause:
Explicit Deny in S3 Bucket Policy overriding IAM Allow permissions.

---

## ⚙️ AWS Evaluation Order
1. Explicit Deny (Highest Priority)  
2. IAM Allow  
3. Bucket Policy Allow  
4. Default Deny  

---

## 🛠️ Phase 5: Resolution
- Removed/modifed Explicit Deny rule  
- Retested access via AWS CLI  
- Verified successful access restoration  

✔ Issue resolved successfully

---

## 🚨 Impact
- S3 object became inaccessible via browser and CLI  
- Simulated real-world production access failure  

---

## 🧠 Key Learnings
- IAM and S3 Bucket Policy work as separate layers  
- Explicit Deny overrides all Allow rules  
- 403 errors require multi-layer debugging  
- Cloud troubleshooting requires structured analysis  

---

## 🚀 Outcome
Demonstrated real-world AWS Cloud Support skills:
- Incident analysis  
- Root cause identification  
- IAM vs resource policy debugging  
- AWS permission model understanding  

---

## 👨‍💻 Author
AWS Cloud Learning Portfolio  
Focus: Cloud Support Engineer Preparation  
