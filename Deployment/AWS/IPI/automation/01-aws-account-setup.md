# 01 — AWS account and CLI setup

## Objective

Prepare approved AWS access and verify the AWS CLI is using the intended account and region.

## Install AWS CLI v2 (Linux x86_64)

Use the official AWS installation instructions and verify the downloaded package before installing it.

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

## Configure credentials

Prefer an approved IAM role or AWS IAM Identity Center/short-lived credentials when available. If your organization requires `aws configure`, enter credentials interactively on your secured workstation only. **Do not put access keys or secret keys in this file, Git, shell history, or screenshots.**

```bash
aws configure
```

Verify the active identity and region:

```bash
aws sts get-caller-identity
aws configure get region
aws ec2 describe-availability-zones --region ap-south-1
```

Replace `ap-south-1` if your deployment uses another region.

## Permissions

Use the current Red Hat documentation for the selected OpenShift release to determine required AWS permissions. IPI generally needs permissions to create and manage relevant compute, networking, IAM, DNS, load-balancing, and storage resources. Avoid assuming a short list of service names is sufficient.

## Checklist

- [ ] AWS account/subscription approved for this deployment
- [ ] Active identity verified with `aws sts get-caller-identity`
- [ ] Intended region confirmed
- [ ] Required permissions reviewed against release-specific Red Hat documentation
- [ ] Credentials are not stored in Git
