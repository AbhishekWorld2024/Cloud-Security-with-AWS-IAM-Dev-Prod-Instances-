# Cloud-Security-with-AWS-IAM-Dev-Prod-Instances-

secure-cloud-infra-aws-iam/<br>
│
├── README.md       <br>               ← Full documentation
├── architecture/<br>
│   ├── diagram.png  <br>              ← Visual representation of the architecture
│   └── design-decisions.md <br> <br>     ← Notes about choices made
│
├── iam-policies/<br>
│   ├── dev-ec2-role-policy.json<br>
│   ├── prod-ec2-role-policy.json<br>
│   ├── dev-bucket-policy.json<br>
│   └── prod-bucket-policy.json<br><br>
│
├── scripts/<br>
│   ├── dev-upload-test.sh  <br>      ← Sample command to test upload from Dev EC2
│   └── prod-read-test.sh    <br>     ← Sample read test from Prod EC2
│
└── setup-guide/<br>
    ├── ec2-role-attach.md <br>       ← Steps to attach IAM roles to EC2
    └── s3-policy-setup.md  <br>  <br>    ← Guide to apply bucket policies

 
 Core AWS Services Used<br>
Component	Description<br>
EC2 (Dev)	Represents a developer’s machine (t2.micro) with IAM role to upload to Dev bucket<br>
EC2 (Prod)	Represents a production instance with read-only access to Prod bucket<br>
S3 (Dev Bucket)	For test files/logs from developers<br>
S3 (Prod Bucket)	For real app data – strictly protected<br>
IAM Roles	Fine-grained access policies scoped to EC2<br>
S3 Bucket Policies	Reinforce security by checking who is allowed or denied<br><br>
