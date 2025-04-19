# Cloud-Security-with-AWS-IAM-Dev-Prod-Instances-

<h2>Secure Multi-Environment AWS Infrastructure</h2>

<p>
Designed and implemented a secure, multi-environment infrastructure on AWS that strictly separates development and production workloads. The architecture includes two Amazon EC2 instances—one for development and another for production—each configured with fine-grained IAM roles and tailored S3 access policies to uphold the principles of least privilege and defense-in-depth.
</p>

<h3>✅ Key Highlights:</h3>

<ul>
  <li>
    <strong>🔐 IAM-Based Access Control:</strong> Assigned tightly scoped IAM roles to each EC2 instance, ensuring that developers have the necessary permissions to upload and test files in the Dev S3 bucket, while the production instance operates with read-only or zero access, depending on the environment.
  </li>
  <li>
    <strong>🪪 S3 Bucket Policies:</strong> Applied custom S3 bucket policies to reinforce security at the bucket level, explicitly denying access from production to Dev buckets and vice versa, preventing any unintended lateral movement between environments.
  </li>
  <li>
    <strong>🚫 No Static Credentials:</strong> Ensured zero use of hardcoded or static AWS credentials by leveraging IAM roles attached directly to EC2 instances for secure, temporary access.
  </li>
  <li>
    <strong>🧱 Environment Isolation:</strong> Established a strong boundary between Dev and Prod by restricting S3 access only to what is necessary per role, preventing any data leakage or unauthorized access.
  </li>
</ul>

<p>
This project demonstrates a security-first approach to cloud infrastructure design, with an emphasis on environment segregation, role-based access control, and AWS-native security features.
</p>

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

 
 <h2>🧰 Core AWS Services Used</h2> 
<table>
  <thead>
    <tr>
      <th>Component</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>EC2 (Dev)</td>
      <td>Represents a developer’s machine (<code>t2.micro</code>) with IAM role to upload to Dev bucket</td>
    </tr>
    <tr>
      <td>EC2 (Prod)</td>
      <td>Represents a production instance with read-only access to Prod bucket</td>
    </tr>
    <tr>
      <td>S3 (Dev Bucket)</td>
      <td>For test files/logs from developers</td>
    </tr>
    <tr>
      <td>S3 (Prod Bucket)</td>
      <td>For real app data – strictly protected</td>
    </tr>
    <tr>
      <td>IAM Roles</td>
      <td>Fine-grained access policies scoped to EC2</td>
    </tr>
    <tr>
      <td>S3 Bucket Policies</td>
      <td>Reinforce security by checking who is allowed or denied</td>
    </tr>
  </tbody>
</table>



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

