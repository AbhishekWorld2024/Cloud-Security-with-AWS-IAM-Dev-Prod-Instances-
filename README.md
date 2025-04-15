# Cloud-Security-with-AWS-IAM-Dev-Prod-Instances-

secure-cloud-infra-aws-iam/
│
├── README.md                      ← Full documentation
├── architecture/
│   ├── diagram.png                ← Visual representation of the architecture
│   └── design-decisions.md       ← Notes about choices made
│
├── iam-policies/
│   ├── dev-ec2-role-policy.json
│   ├── prod-ec2-role-policy.json
│   ├── dev-bucket-policy.json
│   └── prod-bucket-policy.json
│
├── scripts/
│   ├── dev-upload-test.sh        ← Sample command to test upload from Dev EC2
│   └── prod-read-test.sh         ← Sample read test from Prod EC2
│
└── setup-guide/
    ├── ec2-role-attach.md        ← Steps to attach IAM roles to EC2
    └── s3-policy-setup.md        ← Guide to apply bucket policies

 
 Core AWS Services Used
Component	Description
EC2 (Dev)	Represents a developer’s machine (t2.micro) with IAM role to upload to Dev bucket
EC2 (Prod)	Represents a production instance with read-only access to Prod bucket
S3 (Dev Bucket)	For test files/logs from developers
S3 (Prod Bucket)	For real app data – strictly protected
IAM Roles	Fine-grained access policies scoped to EC2
S3 Bucket Policies	Reinforce security by checking who is allowed or denied
