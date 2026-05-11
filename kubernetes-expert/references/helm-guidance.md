# Helm guidance

Use this file for `Chart.yaml`, `values.yaml`, template structure, and Helm-oriented review guidance.

## Chart structure

From the official Helm docs, a normal chart layout includes:

- `Chart.yaml`
- `README.md`
- `values.yaml`
- optional `values.schema.json`
- `templates/`
- optional `crds/`
- optional `charts/` for dependencies

## `Chart.yaml`

Prefer:

- `apiVersion: v2`
- a valid chart `name`
- semantic `version`
- quoted `appVersion`
- `kubeVersion` when compatibility matters

Helm docs note that additional arbitrary fields are not allowed in `Chart.yaml`; use annotations for custom metadata.

## Values best practices

From the official Helm values best-practices page:

- use lowercase camelCase names for values keys
- prefer flat values unless a nested group is clearly easier to understand
- quote strings to avoid YAML type surprises
- prefer maps over positional lists when users may override settings with `--set`
- document each value in `values.yaml`

## Template guidance

- keep helpers in `templates/_helpers.tpl`
- keep template conditionals small and readable
- use named ports when a Service, probe, or Ingress refers to a port
- avoid embedding secrets directly in chart defaults
- keep rendered objects close to plain Kubernetes manifests so upstream docs still apply

## Opinionated platform conventions for this skill

- Default to tenant-safe charts unless the user explicitly asks for platform bootstrap or cluster-wide objects.
- Call out every cluster-scoped resource in the chart review. Do not treat CRDs, ClusterRoles, ClusterRoleBindings, webhooks, or namespace mutations as ordinary app-chart details.
- Prefer explicit chart values or documented conventions for service account behavior, resource requests and limits, probes, and rollout safety.
- Do not hide privileged defaults behind innocuous names or disabled-by-default comments; describe the blast radius plainly.
- If a chart assumes NetworkPolicy enforcement, Pod Security Admission, or quota behavior, say so explicitly in the review.

## CRD caveats

Official Helm chart docs state:

- CRDs belong in `crds/`
- CRDs in `crds/` are plain YAML, not templated
- Helm installs CRDs before normal templates
- Helm does not automatically upgrade or delete CRDs from `crds/`

## Validation workflow

Recommended commands:

```bash
helm lint ./chart
helm template ./chart
```

If install-time behavior matters, add a dry-run step before any real upgrade guidance.

## Version note

The current Helm chart-structure page warns that some content may lag Helm 4 updates. Use the common chart layout and values practices that remain valid for normal Helm 3 and Helm 4 workflows, and state version uncertainty when it matters.

## If the user asks for a chart skeleton

Generate a minimal chart layout rooted in `Chart.yaml` and include only the files required for the user's case. Do not assume a bundled starter chart exists.
