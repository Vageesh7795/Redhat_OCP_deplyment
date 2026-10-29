# 03 — AWS quota check

## Objective

Verify service quotas and available capacity before provisioning.

Example: query an EC2 vCPU quota. Confirm the quota code and applicable instance-family quota in the AWS Service Quotas console or current AWS documentation; quota codes can vary by quota type.

```bash
aws service-quotas list-service-quotas \
  --service-code ec2 \
  --region ap-south-1
```

Example query using a quota code only after confirming it is the relevant quota for your account and instance family:

```bash
aws service-quotas get-service-quota \
  --service-code ec2 \
  --quota-code L-1216C47A \
  --region ap-south-1
```

Also verify instance availability, Elastic IP limits, VPC/network limits, load balancer limits, and storage limits required by the chosen architecture. OpenShift's actual requirements depend on the release, topology, and instance types.

## Checklist

- [ ] EC2 vCPU quota checked for relevant instance families
- [ ] Required instance types available in the selected region/AZs
- [ ] Elastic IP, VPC, subnet, and load-balancer quotas reviewed
- [ ] Quota increases requested early if needed
- [ ] Cost estimate reviewed
