# Example: platform review request

## Sample input

Review this namespace onboarding package for a new team in a shared production cluster. We want:

- Pod Security Admission labels
- `ResourceQuota` and `LimitRange`
- default-deny `NetworkPolicy`
- a Deployment and Service
- minimal RBAC
- safe rollout and node-drain behavior

Tell me whether this is safe for a shared cluster and what you would change.

## Expected behavior

- identify blast radius first, especially any cluster-scoped objects
- review Pod Security, RBAC scope, service account token use, requests and limits, quota fit, and NetworkPolicy assumptions
- explain whether a PodDisruptionBudget is appropriate and what it does not guarantee
- return a safer platform-oriented variant and validation steps
