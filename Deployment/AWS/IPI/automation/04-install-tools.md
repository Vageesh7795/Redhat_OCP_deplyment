# 04 — Install OpenShift tools

## Objective

Install `openshift-install` and `oc`/`kubectl` versions that match the target OpenShift release.

**Important:** do not blindly use `latest` for a production deployment. Choose and record the exact supported OpenShift release, then download the corresponding client and installer from the official Red Hat mirror.

Example download pattern (replace `VERSION` with the selected release directory/version and verify the current official URL):

```bash
# Download the installer and client archives for the same chosen OpenShift release.
# Use the exact URLs published by the official Red Hat mirror.
tar -xzf openshift-install-linux.tar.gz
tar -xzf openshift-client-linux.tar.gz

chmod +x openshift-install oc kubectl
sudo install -m 0755 openshift-install oc kubectl /usr/local/bin/
```

Verify:

```bash
openshift-install version
oc version --client
kubectl version --client
```

If the downloaded archive extracts into a different directory, adjust the commands to match the actual extracted paths.

## Checklist

- [ ] Target OpenShift release recorded
- [ ] Installer and client versions match the target release
- [ ] Tools installed and version output verified
