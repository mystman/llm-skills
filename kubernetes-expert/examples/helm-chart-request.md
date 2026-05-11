# Example: Helm chart request

## Sample input

Create a Helm chart skeleton for a stateless API with:

- Deployment and ClusterIP Service
- optional Ingress
- documented `values.yaml`
- `values.schema.json`
- a reusable helper template

## Expected behavior

- return a chart layout rooted in `Chart.yaml`
- use `apiVersion: v2`
- prefer camelCase values keys
- explain any assumptions about image, ports, and ingress
- recommend `helm lint` and `helm template` before install
