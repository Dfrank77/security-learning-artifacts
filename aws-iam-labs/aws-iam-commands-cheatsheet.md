# AWS IAM Commands Cheat Sheet

Essential AWS CLI commands for IAM security work

---

## AWS Organizations

### List Organizations Structure
```bash
# Show organization details
aws organizations describe-organization

# List all accounts
aws organizations list-accounts

# List OUs under root
aws organizations list-organizational-units-for-parent --parent-id r-XXXX

# List accounts in an OU
aws organizations list-accounts-for-parent --parent-id ou-XXXX
```

### Service Control Policies (SCPs)
```bash
# List all SCPs
aws organizations list-policies --filter SERVICE_CONTROL_POLICY

# Get SCP details
aws organizations describe-policy --policy-id p-XXXX

# Create SCP
aws organizations create-policy \
  --name "PolicyName" \
  --description "Description" \
  --content file://policy.json \
  --type SERVICE_CONTROL_POLICY

# Attach SCP to OU
aws organizations attach-policy --policy-id p-XXXX --target-id ou-XXXX

# List policies attached to an OU
aws organizations list-policies-for-target --target-id ou-XXXX --filter SERVICE_CONTROL_POLICY

# Detach SCP
aws organizations detach-policy --policy-id p-XXXX --target-id ou-XXXX

# Delete SCP
aws organizations delete-policy --policy-id p-XXXX
```

---

## IAM Users & Groups

### Users
```bash
# List all IAM users
aws iam list-users

# Get user details
aws iam get-user --user-name USERNAME

# Create user
aws iam create-user --user-name USERNAME

# Delete user
aws iam delete-user --user-name USERNAME

# List user's policies
aws iam list-attached-user-policies --user-name USERNAME
aws iam list-user-policies --user-name USERNAME

# Attach policy to user
aws iam attach-user-policy --user-name USERNAME --policy-arn arn:aws:iam::aws:policy/PolicyName
```

### Groups
```bash
# List all groups
aws iam list-groups

# Create group
aws iam create-group --group-name GROUPNAME

# Add user to group
aws iam add-user-to-group --user-name USERNAME --group-name GROUPNAME

# List users in group
aws iam get-group --group-name GROUPNAME

# Attach policy to group
aws iam attach-group-policy --group-name GROUPNAME --policy-arn POLICY_ARN
```

---

## IAM Roles

### Basic Role Commands
```bash
# List all roles
aws iam list-roles

# Get role details
aws iam get-role --role-name ROLENAME

# Create role (requires trust policy)
aws iam create-role --role-name ROLENAME --assume-role-policy-document file://trust-policy.json

# Delete role
aws iam delete-role --role-name ROLENAME

# List policies attached to role
aws iam list-attached-role-policies --role-name ROLENAME

# Attach policy to role
aws iam attach-role-policy --role-name ROLENAME --policy-arn POLICY_ARN
```

### Assume Role
```bash
# Assume a role (get temporary credentials)
aws sts assume-role --role-arn arn:aws:iam::ACCOUNT_ID:role/ROLENAME --role-session-name SESSION_NAME
```

---

## IAM Policies

### Managed Policies
```bash
# List AWS managed policies
aws iam list-policies --scope AWS

# List customer managed policies
aws iam list-policies --scope Local

# Get policy details
aws iam get-policy --policy-arn POLICY_ARN

# Get policy version (actual JSON)
aws iam get-policy-version --policy-arn POLICY_ARN --version-id v1

# Create policy
aws iam create-policy --policy-name POLICYNAME --policy-document file://policy.json

# Delete policy
aws iam delete-policy --policy-arn POLICY_ARN
```

### Inline Policies
```bash
# List inline policies for user
aws iam list-user-policies --user-name USERNAME

# Get inline policy document
aws iam get-user-policy --user-name USERNAME --policy-name POLICYNAME

# Put (create/update) inline policy
aws iam put-user-policy --user-name USERNAME --policy-name POLICYNAME --policy-document file://policy.json

# Delete inline policy
aws iam delete-user-policy --user-name USERNAME --policy-name POLICYNAME
```

---

## IAM Access Analyzer

### Setup
```bash
# Create analyzer (account-level)
aws accessanalyzer create-analyzer --analyzer-name NAME --type ACCOUNT

# Create analyzer (organization-level)
aws accessanalyzer create-analyzer --analyzer-name NAME --type ORGANIZATION

# List analyzers
aws accessanalyzer list-analyzers
```

### Findings
```bash
# List all findings
aws accessanalyzer list-findings --analyzer-arn ARN

# List only active findings
aws accessanalyzer list-findings --analyzer-arn ARN --filter '{"status":{"eq":["ACTIVE"]}}'

# Get specific finding details
aws accessanalyzer get-finding --analyzer-arn ARN --id FINDING_ID

# Archive (mark as resolved) a finding
aws accessanalyzer update-findings --analyzer-arn ARN --ids FINDING_ID --status ARCHIVED
```

---

## S3 Security

### Bucket Operations
```bash
# List all buckets
aws s3 ls

# Create bucket
aws s3 mb s3://BUCKET_NAME --region REGION

# Delete bucket (must be empty)
aws s3 rb s3://BUCKET_NAME

# Delete bucket with all contents (DANGEROUS!)
aws s3 rb s3://BUCKET_NAME --force
```

### Bucket Policies
```bash
# Get bucket policy
aws s3api get-bucket-policy --bucket BUCKET_NAME

# Put (create/update) bucket policy
aws s3api put-bucket-policy --bucket BUCKET_NAME --policy file://policy.json

# Delete bucket policy
aws s3api delete-bucket-policy --bucket BUCKET_NAME
```

### Block Public Access
```bash
# Get block public access settings
aws s3api get-public-access-block --bucket BUCKET_NAME

# Enable block public access (SECURE)
aws s3api put-public-access-block --bucket BUCKET_NAME --public-access-block-configuration \
  "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"

# Disable block public access (INSECURE - lab only)
aws s3api delete-public-access-block --bucket BUCKET_NAME
```

---

## CloudTrail (Audit Logs)

### Trail Operations
```bash
# List trails
aws cloudtrail list-trails

# Get trail details
aws cloudtrail get-trail-status --name TRAIL_NAME

# Lookup recent events
aws cloudtrail lookup-events --max-results 10

# Lookup events by user
aws cloudtrail lookup-events --lookup-attributes AttributeKey=Username,AttributeValue=USERNAME
```

---

## STS (Security Token Service)

### Identity Information
```bash
# Get current caller identity (who am I?)
aws sts get-caller-identity

# Decode authorization message
aws sts decode-authorization-message --encoded-message MESSAGE
```

---

## Useful Filters & Formatting

### Using jq for Better Output
```bash
# Get just policy names
aws organizations list-policies --filter SERVICE_CONTROL_POLICY | jq -r '.Policies[].Name'

# Get user names only
aws iam list-users | jq -r '.Users[].UserName'

# Pretty print any JSON
aws iam get-user --user-name USERNAME | jq

# Get specific field
aws sts get-caller-identity | jq -r '.Account'
```

### Common Filters
```bash
# Filter IAM users by path
aws iam list-users --path-prefix /admins/

# Filter policies by scope
aws iam list-policies --scope Local  # Customer managed only
aws iam list-policies --scope AWS     # AWS managed only
```

---

## Quick Troubleshooting

### Permission Issues
```bash
# Check what identity you're using
aws sts get-caller-identity

# Test if you can perform an action (dry run)
aws ec2 run-instances --dry-run --image-id ami-12345 --instance-type t2.micro
```

### Policy Simulation
```bash
# Simulate IAM policy (requires policy ARN)
aws iam simulate-principal-policy \
  --policy-source-arn arn:aws:iam::ACCOUNT:user/USERNAME \
  --action-names s3:GetObject \
  --resource-arns arn:aws:s3:::bucket-name/*
```

---

## Common Workflows

### Investigate Access Denied
```bash
# 1. Check who you are
aws sts get-caller-identity

# 2. Check your policies
aws iam list-attached-user-policies --user-name YOUR_USERNAME

# 3. Check for SCPs (if in an org)
aws organizations list-policies-for-target --target-id ACCOUNT_ID --filter SERVICE_CONTROL_POLICY

# 4. Check CloudTrail for the denied action
aws cloudtrail lookup-events --lookup-attributes AttributeKey=EventName,AttributeValue=ACTION_NAME
```

### Audit MFA Usage
```bash
# List users without MFA
aws iam get-credential-report  # Must generate first
aws iam generate-credential-report
aws iam get-credential-report --output text | grep "false" | cut -f1
```

### Find Unused Credentials
```bash
# List access keys for all users
aws iam list-users | jq -r '.Users[].UserName' | while read user; do
  aws iam list-access-keys --user-name $user
done
```

---

## Aliases for Efficiency

Add these to your ~/.zshrc or ~/.bashrc:
```bash
# IAM shortcuts
alias iam-users='aws iam list-users | jq -r ".Users[] | {UserName, CreateDate}"'
alias iam-roles='aws iam list-roles | jq -r ".Roles[] | {RoleName, CreateDate}"'
alias whoami='aws sts get-caller-identity | jq'

# Organizations shortcuts
alias org-accounts='aws organizations list-accounts | jq ".Accounts[] | {Name, Id, Email}"'
alias org-policies='aws organizations list-policies --filter SERVICE_CONTROL_POLICY | jq -r ".Policies[] | [.Name, .Id] | @tsv" | column -t'

# Access Analyzer shortcuts (replace ARN)
alias analyzer-findings='aws accessanalyzer list-findings --analyzer-arn YOUR_ARN | jq'
```

---

## Tips

1. **Always use jq** for readable JSON output
2. **Use --dry-run** when available to test commands safely
3. **Pipe to less** for long output: `aws iam list-users | jq | less`
4. **Use --query** for AWS CLI filtering (alternative to jq)
5. **Check help** for any command: `aws iam create-user help`

---

**Last Updated:** December 2024
