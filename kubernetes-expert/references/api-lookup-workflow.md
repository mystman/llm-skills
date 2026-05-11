# API lookup workflow

Use this workflow for questions such as “what fields are required,” “what is the right apiVersion,” or “is this resource namespaced?”

## 1) Identify the resource

Determine:

- `kind`
- `apiVersion` if already present
- whether the resource is built-in Kubernetes or a CRD

If the resource comes from an operator or vendor API group, say that the official Kubernetes API reference will not define that schema.

## 2) Determine group, version, and scope

Check the Kubernetes API group index first, then the generated API reference.

Return:

- group and version
- namespaced vs cluster-scoped
- whether the version appears deprecated or migrated

## 3) Use the right source for the right question

- Use the API overview for semantics, versioning, and server behavior.
- Use the generated API reference for concrete field names and nested structures.
- Use resource-specific docs when lifecycle or controller behavior matters.

## 4) Prefer targeted lookups

The generated API reference is large. Search for the exact resource and version, such as:

- `apps/v1 Deployment`
- `v1 Service`
- `networking.k8s.io/v1 Ingress`

If local tooling is available, `kubectl explain <resource>` and `kubectl explain <resource>.<field>` can validate field placement.

## 5) Return a minimal valid example

When the user asks field-level questions, include a small example manifest that shows only the required and most relevant fields.

## 6) Deprecation and migration rules

- If the user provides an old apiVersion, say whether it is likely deprecated and why that matters.
- Do not change an apiVersion without explaining the cluster-version assumption.
- If the version is unknown, say the answer targets current upstream docs.

## Common pitfalls to call out

- `selector` mismatches in Deployments and Services
- controller-specific annotations on Ingress resources
- mixing cluster-scoped and namespaced resources in one explanation
- assuming CRD fields are documented in the core Kubernetes API reference
- treating status fields as user-settable spec fields
