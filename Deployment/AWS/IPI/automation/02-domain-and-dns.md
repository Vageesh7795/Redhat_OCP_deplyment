# 02 — Domain and DNS

## Objective

Confirm domain ownership and DNS delegation before installation.

Use a domain that you own or are authorized to administer. Example values below are placeholders; replace them with your actual registered domain and cluster base domain.

```bash
nslookup example.com
dig NS example.com
```

To check the parent delegation, query the authoritative DNS chain as appropriate for your domain:

```bash
dig +trace NS example.com
```

Do not use a leading dot before the domain name in the `dig NS` command.

## Route 53

Route 53 can host DNS records, but creating a hosted zone alone does not make a public domain resolvable. The registered domain's nameservers must be delegated to the hosted zone's assigned nameservers at the registrar/parent DNS provider.

For AWS IPI, confirm the DNS and domain requirements for your exact OpenShift release and `publish` setting.

## Checklist

- [ ] Domain ownership/authorization confirmed
- [ ] Correct base domain chosen
- [ ] Hosted-zone nameservers checked
- [ ] Registrar/parent delegation verified
- [ ] DNS queries resolve as expected
