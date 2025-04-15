# Cloud-Security-with-AWS-IAM-Dev-Prod-Instances-

secure-cloud-infra-aws-iam/<br>
│
├── README.md       <br>               
├── architecture/<br>
│   ├── diagram.png  <br>              
│   └── design-decisions.md <br> <br>     
│
├── iam-policies/<br>
│   ├── dev-ec2-role-policy.json<br>
│   ├── prod-ec2-role-policy.json<br>
│   ├── dev-bucket-policy.json<br>
│   └── prod-bucket-policy.json<br><br>
│
├── scripts/<br>
│   ├── dev-upload-test.sh  <br>      
│   └── prod-read-test.sh    <br>     
│
└── setup-guide/<br>
    ├── ec2-role-attach.md <br>      
    └── s3-policy-setup.md  <br>  <br>   

 
 Core AWS Services Used<br>
Component	Description<br>
EC2 (Dev)	Represents a developer’s machine (t2.micro) with IAM role to upload to Dev bucket<br>
EC2 (Prod)	Represents a production instance with read-only access to Prod bucket<br>
S3 (Dev Bucket)	For test files/logs from developers<br>
S3 (Prod Bucket)	For real app data – strictly protected<br>
IAM Roles	Fine-grained access policies scoped to EC2<br>
S3 Bucket Policies	Reinforce security by checking who is allowed or denied<br><br>


<h2>🔍 Real-World Security Goals</h2>

<table>
  <thead>
    <tr>
      <th>Security Scenario</th>
      <th>Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Dev EC2 uploads to dev bucket</td>
      <td>✅ Allowed</td>
    </tr>
    <tr>
      <td>Dev EC2 tries accessing prod bucket</td>
      <td>❌ Denied</td>
    </tr>
    <tr>
      <td>Prod EC2 reads from prod bucket</td>
      <td>✅ Allowed</td>
    </tr>
    <tr>
      <td>Prod EC2 uploads or deletes files</td>
      <td>❌ Denied</td>
    </tr>
    <tr>
      <td>No hardcoded AWS credentials</td>
      <td>✅ IAM roles used</td>
    </tr>
    <tr>
      <td>External access blocked unless authorized</td>
      <td>✅ Bucket policy enforced</td>
    </tr>
  </tbody>
</table>

