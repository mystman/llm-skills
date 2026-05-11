# Troubleshooting playbooks

Use this file when the user reports failures such as `CrashLoopBackOff`, `Pending`, no Service endpoints, failing rollouts, admission denials, drain blockers, or PVC binding issues.

## First-pass triage

Prefer this sequence:

1. identify the exact failing resource
2. inspect current state and events
3. inspect logs or rollout status
4. inspect dependent resources such as Service selectors, PVCs, ConfigMaps, Secrets, Ingress, ServiceAccounts, RBAC, NetworkPolicy, PDB, ResourceQuota, or LimitRange
5. rank likely causes instead of guessing a single cause too early

Common safe commands to recommend:

```bash
kubectl get pods -n <namespace>
kubectl describe pod <pod> -n <namespace>
kubectl logs <pod> -n <namespace> --previous
kubectl get events -n <namespace> --sort-by=.lastTimestamp
kubectl rollout status deployment/<name> -n <namespace>
kubectl get resourcequota,limitrange,networkpolicy,pdb,serviceaccount,rolebinding -n <namespace>
```

## Symptom map

### `CrashLoopBackOff`

Check:

- container exit code and `lastState`
- app logs and previous logs
- command and args
- ConfigMap or Secret mounts and env refs
- liveness, readiness, and startup probes
- OOMKilled signals and resource limits

Common causes:

- bad entrypoint or missing dependency
- probe path or port mismatch
- startup takes longer than probe thresholds
- missing config or credentials
- process exits immediately by design

### `ImagePullBackOff` or `ErrImagePull`

Check:

- image repository, tag, and spelling
- imagePullSecrets and registry access
- network reachability and rate limits
- architecture mismatch or nonexistent tag

### `Pending`

Check:

- scheduler events
- requests and limits vs cluster capacity
- node selectors, affinity, taints, and tolerations
- PVC binding state
- quota or limit-range restrictions

Common causes:

- unschedulable resource requests
- missing tolerations
- unbound PVC
- strict affinity rules with no matching nodes

### Admission denied or create rejected

Check:

- Pod Security Admission labels and violations
- ResourceQuota or LimitRange rejections
- invalid security context or forbidden host access
- missing namespace labels or policy prerequisites

Common causes:

- Pod Security Standards rejecting privileged or non-compliant pods
- quota exceeded or missing required requests and limits
- cluster policy blocking unsafe defaults

### `CreateContainerConfigError` or `CreateContainerError`

Check:

- missing ConfigMaps or Secrets
- bad env or volume references
- invalid command or volume mounts

### Service has no endpoints

Check:

- Service selector vs pod labels
- readiness state of backing pods
- `targetPort` vs container port name or number
- namespace mismatch

### Ingress routes do not work

Check:

- IngressClass and controller in use
- backend Service name and port
- endpoint readiness
- path and host rules
- TLS secret and DNS assumptions
- controller-specific annotations

### PVC stuck in `Pending`

Check:

- StorageClass name
- provisioner availability
- access mode support
- requested size and topology constraints

### `Forbidden` from the Kubernetes API

Check:

- ServiceAccount name on the pod
- Role, ClusterRole, RoleBinding, and ClusterRoleBinding coverage
- namespace scope vs cluster scope
- whether the action depends on escalation-sensitive permissions such as `bind`, `escalate`, `impersonate`, token minting, or node proxy access

### Node drain, upgrade, or eviction blocked

Check:

- PodDisruptionBudget selectors and current healthy replica count
- readiness state and replica math
- singleton or quorum workload behavior

Common causes:

- overly strict PDB
- too few healthy replicas to satisfy `minAvailable`
- misunderstanding that PDB covers only voluntary disruptions

### Network path blocked in shared cluster

Check:

- NetworkPolicy objects in source and destination namespaces
- whether the cluster CNI enforces NetworkPolicy at all
- DNS egress allowances and namespace label selectors

Common causes:

- default-deny policy without explicit allow rule
- namespace selector mismatch
- assuming NetworkPolicy is enforced when the CNI ignores it

### Deployment rollout not progressing

Check:

- rollout events and conditions
- image pull issues
- readiness probe failures
- unavailable replicas due to PDB or scheduling
- immutable field changes such as selectors
- quota or policy blockers preventing replacement pods

## Response contract

For troubleshooting answers, return:

1. ranked hypotheses
2. evidence already present
3. missing evidence still needed
4. safest next checks or commands
5. recommended fix and how to validate it
6. blast radius or tenant impact of the fix

## Guardrail

If the user gives only a symptom with no manifests, events, or logs, ask for the smallest high-signal artifact instead of guessing.
