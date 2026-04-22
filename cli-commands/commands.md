# AWS CLI Commands Used in This Project

---

## 🟢 Setup & Verification

aws configure → Used to configure AWS CLI with Access Key, Secret Key, Region, and output format.

aws sts get-caller-identity → Confirms IAM user identity (s3-debug-user) and verifies CLI authentication.

aws s3 ls → Lists all S3 buckets to verify S3 access is working with IAM permissions.

---

## 🟢 Baseline Check

aws s3 ls s3://s3-lab-403 → Checks contents of the S3 bucket and confirms baseline access.

aws s3 cp s3://s3-lab-403/index.html . → Downloads file successfully before incident.

---

## ❌ Incident (Failure State)

aws s3 cp s3://s3-lab-403/index.html . → Returns AccessDenied (403 Forbidden) due to Explicit Deny in bucket policy.

---

## 🛠️ After Fix (Verification)

aws s3 cp s3://s3-lab-403/index.html . → Successfully downloads file after policy fix.

aws s3 ls s3://s3-lab-403 → Final verification of restored access.