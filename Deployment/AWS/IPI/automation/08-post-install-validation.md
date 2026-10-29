# 08 — Post-install validation

## Set kubeconfig

The installer creates the kubeconfig under the installation directory's `auth` folder. Set the path for the current shell:

```bash
export KUBECONFIG="$PWD/clusterconfig/auth/kubeconfig"
oc whoami
```

## Validate cluster health

```bash
oc get nodes -o wide
oc get clusterversion
oc get clusteroperators
oc get pods -A
```

Check that nodes become `Ready`, the cluster version reports the expected release, and cluster operators settle into healthy states. Investigate any degraded or unavailable operators before handover.

## Console access

Retrieve the initial kubeadmin password from the protected installation directory:

```bash
cat clusterconfig/auth/kubeadmin-password
```

Find the console route:

```bash
oc get route console -n openshift-console
```

Open the route shown by the command and sign in using `kubeadmin` and the generated password, if that account is enabled for your installation workflow. Follow your organization's procedure to configure identity providers and remove/disable temporary bootstrap credentials as appropriate.

## Record deployment facts

Record sanitized values in the deployment record:
- OpenShift version and cluster name
- API and console URLs
- Node names, roles, and instance types
- DNS, network, load balancer, and storage details
- Validation results and known issues

Never commit kubeconfig, kubeadmin password, pull secret, private keys, or unredacted logs.

## Checklist

- [ ] Nodes are Ready
- [ ] Cluster version is as expected
- [ ] Cluster operators are healthy
- [ ] Console and API access tested
- [ ] DNS and ingress tested
- [ ] Storage validation completed
- [ ] Sanitized deployment record and handover completed
