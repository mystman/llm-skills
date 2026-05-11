# Platform guardrails

Use this file when reviewing changes for a shared or production cluster.

## Shared-cluster default

- Treat namespaces as the basic tenancy unit, not as sufficient isolation on their own.
- For tenant safety, consider namespaces together with RBAC, NetworkPolicy, Pod Security controls, quotas, and workload-level hardening.
- Prefer namespace-scoped changes and explicitly call out the blast radius of cluster-scoped resources.

## RBAC defaults

- Prefer `Role` and `RoleBinding` over `ClusterRoleBinding` when possible.
- Avoid wildcard verbs or resources, routine `cluster-admin`, and especially `system:masters`.
- Treat the following as escalation-sensitive and exceptional: `bind`, `escalate`, `impersonate`, `serviceaccounts/token`, `nodes/proxy`, CSR approval, webhook configuration, and namespace label mutation.
- Default `automountServiceAccountToken: false` unless the workload actually needs Kubernetes API access.

## Pod security defaults

- `Baseline` blocks common privilege-escalation paths such as privileged containers, host namespaces, and Windows HostProcess.
- `Restricted` is the default target for normal tenant workloads when compatible: non-root execution, no privilege escalation, seccomp `RuntimeDefault` or `Localhost`, minimal capabilities, and limited volume types.
- These standards are not complete security by themselves, and some controls are Linux-only or version-sensitive.

## Network and tenancy

- Prefer default-deny ingress and egress with explicit allow rules.
- Only describe NetworkPolicy as effective isolation if the cluster networking implementation enforces it.
- When strong tenant isolation is required, mention that storage isolation, node isolation, sandboxing, virtual control planes, or separate clusters may be necessary.

## Availability and rollout safety

- PodDisruptionBudgets only limit voluntary disruptions; they do not guarantee uptime and do not cover all outage modes.
- For controller-managed workloads, `maxUnavailable` often adapts better than fixed `minAvailable` when replica counts change.
- Percentage-based PDB rounding is upward, which matters for small replica counts.
- Pair PDB guidance with probes, rollout strategy, replica math, and drain planning.

## Quotas and defaults

- Use `ResourceQuota` per namespace and pair it with `LimitRange` when CPU and memory defaults are needed.
- Quotas do not retroactively modify existing objects and do not scale automatically with cluster growth.
- Object-count quotas can protect the control plane and namespace hygiene for resources like Secrets, Jobs, and PVCs.

## Response contract

For platform-facing reviews, always separate:

1. blast radius
2. security and tenancy findings
3. rollout and availability findings
4. safer recommended variant
5. validation and rollback plan
