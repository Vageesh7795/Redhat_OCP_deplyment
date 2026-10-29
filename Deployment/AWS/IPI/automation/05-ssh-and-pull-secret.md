# 05 — SSH key and pull secret

## SSH key

Generate a key pair in a secure working directory. Use your organization's approved key type and security policy.

```bash
ssh-keygen -t ed25519 -f ./openshift-key -N ""
```

If the target environment or policy requires RSA, use the approved RSA command instead. Keep `openshift-key` private and out of Git; only the public key is supplied to the installer.

```bash
cat ./openshift-key.pub
```

## Pull secret

Obtain the pull secret from the official Red Hat OpenShift Cluster Manager for the target cluster. Treat it as a credential. Do not paste it into Markdown, source control, tickets, or logs.

The installer prompts for the pull secret when generating `install-config.yaml`. Keep generated configuration private because it contains sensitive installation values.

## Checklist

- [ ] SSH key pair generated in a secure directory
- [ ] Private key excluded from Git and backed up securely
- [ ] Pull secret obtained from the official source
- [ ] Secret-bearing files stored outside source control
