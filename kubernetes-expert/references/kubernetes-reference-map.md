# Kubernetes reference map

Use this file to decide which official source to consult first.

## Core upstream sources

- Reference index: https://kubernetes.io/docs/reference/
- API overview: https://kubernetes.io/docs/reference/using-api/
- Kubernetes API group index: https://kubernetes.io/docs/reference/kubernetes-api/
- Generated API reference: https://kubernetes.io/docs/reference/generated/kubernetes-api/latest/

## Quick mapping

| User need | Start here | Then use | Notes |
| --- | --- | --- | --- |
| Exact field definitions | Generated API reference | API overview | Best for `spec.*` and `status.*` field details |
| Correct `apiVersion` and resource family | Kubernetes API group index | Deprecation or migration docs | Important for older manifests |
| Concept explanation | Reference index | Concept pages linked from reference | Use for behavior and lifecycle, not just fields |
| Manifest review | Resource-specific docs | Generated API reference | Check both semantics and field validity |
| Troubleshooting Pods or workloads | Debug tasks and pod lifecycle docs | Probes and resource-management docs | Prefer real events and logs first |
| Platform review, tenancy, or policy design | Pod Security Standards, RBAC good practices, Multi-tenancy, Resource Quotas, Security Checklist | NetworkPolicy and workload docs | Namespaces alone are not enough for isolation |
| Rollout safety and drain planning | Deployment and PDB docs | Probes and scheduling docs | PDBs only cover voluntary disruptions |
| Services, Ingress, networking | Services and networking docs | EndpointSlices, DNS, NetworkPolicy docs | Ask which ingress controller if annotations matter |
| Storage issues | PersistentVolume, PVC, StorageClass docs | StatefulSet storage docs | Check provisioner and access mode assumptions |
| Security and access | Pod Security, ServiceAccounts, RBAC docs | Security checklist | Separate core Kubernetes from external identity systems |
| Helm chart design | Helm charts docs | Helm values best practices | Use Kubernetes docs for rendered resource behavior |

## Resource family shortcuts

- Workloads: Pods, Deployments, StatefulSets, DaemonSets, Jobs, CronJobs
- Networking: Services, Ingress, Gateway API, EndpointSlices, NetworkPolicy, DNS
- Storage: PersistentVolumes, PersistentVolumeClaims, StorageClasses, VolumeSnapshots
- Configuration: ConfigMaps, Secrets, probes, resource requests and limits
- Security: ServiceAccounts, RBAC, Pod Security Standards, admission, multi-tenancy

## Practical lookup rule

Use the API overview when the question is about behavior or API semantics. Use the generated API reference when the question is about exact fields, object shapes, or whether a nested field belongs in a manifest.

## Version sensitivity

If the user shows an older apiVersion, do not silently upgrade it. First confirm the target Kubernetes version and then explain whether migration is recommended or required.

## Platform caveats to keep explicit

- NetworkPolicy requires an enforcing CNI.
- ResourceQuota does not retroactively change objects and does not scale automatically with cluster growth.
- PodDisruptionBudget is not an uptime guarantee.
- Pod Security Standards describe target restrictions; they are not complete security on their own.
