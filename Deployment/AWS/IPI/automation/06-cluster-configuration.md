# 06 — Cluster configuration

## Objective

Generate and review `install-config.yaml` in a dedicated working directory.

```bash
mkdir -p clusterconfig
openshift-install create install-config --dir=clusterconfig
```

Answer the prompts with values approved for the target environment, including AWS platform, region, base domain, cluster name, SSH public key, and pull secret.

## Review configuration

Edit `clusterconfig/install-config.yaml` and validate all values against the documentation for your chosen OpenShift release. Example planning values only:

```yaml
apiVersion: v1
baseDomain: example.com
metadata:
  name: example-cluster
platform:
  aws:
    region: ap-south-1
publish: External
```

The installer-generated file includes additional required fields. **Do not replace the generated file with this abbreviated example.** Preserve the generated `pullSecret` and `sshKey` values; do not leave them blank. Do not commit the real file to Git.

Review instance types, replica counts, networking CIDRs, and architecture with the release-specific requirements. Ensure the machine CIDR does not overlap with connected networks.

Back up the config only in the secured working directory:

```bash
cp clusterconfig/install-config.yaml clusterconfig/install-config.yaml.backup
```

Both files can contain sensitive data. Ensure the directory is excluded from Git.

## Checklist

- [ ] Cluster name and base domain validated
- [ ] Region and instance types confirmed
- [ ] CIDRs checked for overlap
- [ ] Replica counts match intended topology
- [ ] Pull secret and SSH public key populated
- [ ] Generated configuration and backup excluded from Git
