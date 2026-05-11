# Example: API lookup request

## Sample input

What is the right apiVersion and a minimal example for a NetworkPolicy that only allows ingress to pods labeled `app=api` from namespaces labeled `team=payments` on TCP port 8080?

## Expected behavior

- identify `networking.k8s.io/v1`
- state that NetworkPolicy is namespaced
- show the relevant fields: `podSelector`, `policyTypes`, `ingress`, `from`, and `ports`
- provide a minimal manifest
- cite official Kubernetes networking references
