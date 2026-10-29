# AWS IPI deployment runbook

Follow the phase files in numerical order.

1. [AWS account and CLI setup](01-aws-account-setup.md)
2. [Domain and DNS](02-domain-and-dns.md)
3. [AWS quota check](03-aws-quota-check.md)
4. [Install OpenShift tools](04-install-tools.md)
5. [SSH key and pull secret](05-ssh-and-pull-secret.md)
6. [Cluster configuration](06-cluster-configuration.md)
7. [Install the cluster](07-install-cluster.md)
8. [Post-install validation](08-post-install-validation.md)

## Deployment variables to record

- OpenShift release:
- AWS region:
- Cluster name:
- Base domain:
- Machine CIDR:
- Control-plane instance type/count:
- Worker instance type/count:
- Deployment date/change reference:

Keep customer-specific values in an approved private repository. Never commit credentials or secret-bearing files.
