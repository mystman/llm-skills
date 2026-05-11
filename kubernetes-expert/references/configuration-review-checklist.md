# Configuration review checklist

Use this checklist for manifest review, manifest generation, platform onboarding, or configuration hardening guidance in shared clusters.

## Scope and blast radius

- the change is clearly namespaced or clearly justified as cluster-scoped
- cluster-scoped resources such as ClusterRoles, ClusterRoleBindings, CRDs, webhooks, StorageClasses, IngressClasses, or namespace label changes are called out explicitly
- tenant impact and rollback path are described for any platform-wide change

## Core object checks

- `apiVersion` and `kind` are valid for the intended cluster version
- `metadata.name` follows DNS-style naming rules where required
- namespace choice is explicit and appropriate
- labels are consistent and selectors match pod labels exactly

## Tenancy and policy checks

- namespace labels and admission expectations are intentional
- namespaces are not being treated as the only security boundary
- Role and RoleBinding are preferred over wider cluster-scoped grants where possible
- wildcard RBAC rules are absent unless explicitly justified
- service account token mounting is disabled unless Kubernetes API access is needed
- NetworkPolicy expectations match the actual CNI capabilities
- onboarding or tenant namespaces consider `ResourceQuota` and `LimitRange`

## Workload checks

- image repository and tag are explicit enough for the environment
- requests and limits are present when appropriate
- readiness and liveness probes match real ports and paths
- startup probe exists for slow-starting apps when needed
- ports are named consistently when referenced by Services or probes
- rollout strategy and replica count match availability needs
- termination behavior is reasonable for the app

## Security checks

- ServiceAccount choice is intentional
- RBAC is least privilege
- pod and container `securityContext` are explicitly reviewed
- `runAsNonRoot`, dropped capabilities, and `seccompProfile` are considered
- `allowPrivilegeEscalation: false` is considered for normal workloads
- host namespaces, hostPath, privileged mode, and similar escape hatches are justified if present
- no secret literals or private credentials are embedded in examples

## Configuration and dependency checks

- ConfigMaps and Secrets are referenced correctly
- env vars, volume mounts, and projected volumes line up with the app contract
- external dependencies such as databases, DNS names, or ingress controllers are explicit

## Networking checks

- Service selector and target port line up with the workload
- Ingress backend, host, path, class, and TLS settings are coherent
- NetworkPolicy matches the intended traffic model
- default-deny assumptions are made explicit rather than implicit
- readiness state is considered before blaming networking

## Storage checks

- PVC access modes and StorageClass match the backend capabilities
- StatefulSet storage uses `volumeClaimTemplates` when pod identity matters
- reclaim and retention implications are understood

## Operability checks

- rollout or restart impact is acceptable
- logs, metrics, and health endpoints are present or at least planned
- PDB, HPA, or quotas are included when scale and resilience matter
- PodDisruptionBudget is appropriate for the workload type and replica count
- rollout strategy and replica math will not deadlock upgrades or node drains
- admission, quota, or policy failure modes are observable enough to debug

## Helm-specific checks

- `values.yaml` is documented
- values names use lowercase camelCase
- maps are preferred over lists when users are likely to override with `--set`
- strings are quoted when type coercion could surprise users
- `values.schema.json` validates user-facing inputs
- rendered templates use helpers for names and labels where that improves reuse
- app charts do not quietly introduce cluster-scoped or privileged behavior without an explicit callout
- tenant-facing charts expose or document security, resources, probes, and rollout-relevant settings

## Output style

When you review a manifest, separate:

1. blast-radius concerns
2. correctness issues
3. security and tenancy concerns
4. availability and operability issues
5. optional improvements
