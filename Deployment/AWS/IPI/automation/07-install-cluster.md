# 07 — Install the cluster

## Pre-flight

Before starting, confirm the account, region, quotas, DNS, release version, instance types, cost estimate, and change approval. The installer provisions AWS resources and may incur charges.

## Start installation

```bash
openshift-install create cluster --dir=clusterconfig --log-level=info
```

Monitor the installer log in a separate terminal if it exists:

```bash
tail -f clusterconfig/.openshift_install.log
```

The installer may create and configure resources such as networking, compute, security groups, load balancers, DNS records, and bootstrap services according to the configuration and release.

Do not stop or delete resources manually while installation is in progress unless following an approved recovery procedure.

## Checklist

- [ ] Installation started from the intended working directory
- [ ] Installer completed successfully
- [ ] Completion output and generated access files stored securely
- [ ] Actual AWS resources reviewed for unexpected resources or costs
