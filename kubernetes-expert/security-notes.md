# Security notes

Use these rules whenever the skill handles manifests, logs, or operational guidance.

## Sensitive data

- Do not ask the user to paste kubeconfigs, bearer tokens, client certificates, or private keys into chat.
- Do not quote Secret data, base64 values, or registry credentials back to the user.
- Use placeholders such as `<secret-name>` or `<redacted>` in generated examples.

## Operational safety

- Prefer `kubectl diff`, `kubectl apply --dry-run=server`, `helm lint`, and `helm template` before recommending apply, upgrade, restart, or delete actions.
- Call out when a suggestion changes security posture, availability, or stored data.
- Be especially careful with cluster-scoped resources, privileged pods, hostPath mounts, `hostNetwork`, and broad RBAC grants.
- Treat `cluster-admin`, `system:masters`, wildcard RBAC, `bind`, `escalate`, `impersonate`, `nodes/proxy`, and `serviceaccounts/token` as exceptional high-risk capabilities.

## Multi-tenant clusters

- Assume namespaces, node names, hostnames, and internal URLs may be sensitive.
- Prefer namespace-scoped fixes unless the issue clearly requires cluster-wide changes.
- Warn when a recommendation could impact workloads outside the user's namespace.
- Do not present namespaces alone as sufficient isolation; shared clusters usually also need RBAC, quotas, Pod Security, and network isolation.

## Kubernetes-specific reminders

- Pod Security Standards, RBAC, and ServiceAccount choices can change who can access the Kubernetes API and which syscalls or privileges a pod receives.
- Ingress annotations, admission webhooks, service meshes, and operators are often external to core Kubernetes. Confirm the product before giving product-specific advice.
- Helm CRDs placed in `crds/` are not templated and are not automatically upgraded or deleted by Helm.
- NetworkPolicy objects only provide isolation if the cluster networking implementation enforces them.
- PodDisruptionBudgets only limit voluntary evictions; overly strict budgets can block node drains.

## Upstream references

- Pod Security Standards: https://kubernetes.io/docs/concepts/security/pod-security-standards/
- RBAC Good Practices: https://kubernetes.io/docs/concepts/security/rbac-good-practices/
- Secrets Good Practices: https://kubernetes.io/docs/concepts/security/secrets-good-practices/
- Multi-tenancy: https://kubernetes.io/docs/concepts/security/multi-tenancy/
- Security Checklist: https://kubernetes.io/docs/concepts/security/security-checklist/
