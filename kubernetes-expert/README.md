# Kubernetes Expert Skill

Opinionated production and platform-engineering Agent Skills package for Kubernetes on shared clusters.

## Design goals

- Official-docs first
- Shared-cluster and multi-tenant safe defaults
- Version-aware, security-aware, and rollout-aware answers
- Minimal, patch-ready corrections when the user wants code or YAML
- Reusable supporting references and examples for platform teams

## Default assumptions

- The cluster is shared unless the user says otherwise.
- Namespace-scoped and least-privilege options are preferred by default.
- Workloads should usually have explicit requests, limits, probes, and clear rollout behavior.
- Pod Security Standards, RBAC, NetworkPolicy, quotas, and PDBs are treated as controls with caveats, not guarantees.

## Primary references

- Kubernetes Reference: https://kubernetes.io/docs/reference/
- Kubernetes API Overview: https://kubernetes.io/docs/reference/using-api/
- Kubernetes API: https://kubernetes.io/docs/reference/kubernetes-api/
- Generated Kubernetes API Reference: https://kubernetes.io/docs/reference/generated/kubernetes-api/latest/
- Pod Security Standards: https://kubernetes.io/docs/concepts/security/pod-security-standards/
- RBAC Good Practices: https://kubernetes.io/docs/concepts/security/rbac-good-practices/
- Multi-tenancy: https://kubernetes.io/docs/concepts/security/multi-tenancy/
- Resource Quotas: https://kubernetes.io/docs/concepts/policy/resource-quotas/
- PodDisruptionBudget: https://kubernetes.io/docs/tasks/run-application/configure-pdb/
- Security Checklist: https://kubernetes.io/docs/concepts/security/security-checklist/
- Helm Charts: https://helm.sh/docs/topics/charts/
- Helm Values Best Practices: https://helm.sh/docs/chart_best_practices/values/

## Package layout

```text
kubernetes-expert/
├── SKILL.md
├── README.md
├── security-notes.md
├── references/
│   ├── platform-guardrails.md
│   ├── api-lookup-workflow.md
│   ├── configuration-review-checklist.md
│   ├── helm-guidance.md
│   ├── kubernetes-reference-map.md
│   └── troubleshooting-playbooks.md
├── examples/
│   ├── platform-review-request.md
│   ├── api-lookup-request.md
│   ├── helm-chart-request.md
│   ├── manifest-review-request.md
│   ├── missing-context-request.md
│   └── troubleshooting-request.md
```

## How to use

Place `kubernetes-expert/` in your skills directory and register it with your agent if your runtime requires manual skill discovery.

Use the skill when the user asks for any of the following:

- explain a Kubernetes concept or API resource
- review or generate manifests for safer production defaults
- debug Pod, Deployment, Service, Ingress, storage, policy, quota, or RBAC issues
- map a question to the correct Kubernetes API group or field set
- review `Chart.yaml`, `values.yaml`, templates, or Helm release guidance with platform guardrails in mind
- assess tenant isolation, rollout risk, and blast radius before a change

## Included support files

- `references/platform-guardrails.md` captures the skill's opinionated defaults and the upstream caveats behind them.
- `references/` contains reusable playbooks and checklists for common Kubernetes tasks.
- `examples/` shows representative requests and the expected response style.

## Limitations

- This skill is intentionally upstream-first. Controller-specific products still need their own docs.
- The recommendations are intentionally opinionated toward platform teams and shared clusters; single-tenant or system-component workloads may justify different defaults.
- The generated Kubernetes API reference is very large; targeted lookup is better than broad fetching.
- Helm 4 documentation currently warns that some chart-structure content may lag updates, so Helm guidance here sticks to the common subset that remains valid for normal Helm 3 and Helm 4 usage.

## Changelog

- `1.1.0`: shifted the skill from generic Kubernetes help toward an opinionated platform-engineering stance, with stronger guidance on RBAC, Pod Security Standards, multi-tenancy, quotas, disruption budgets, rollout safety, and blast-radius review.
