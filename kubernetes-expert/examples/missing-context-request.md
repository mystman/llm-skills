# Example: missing-context request

## Sample input

Why won't my Service work?

## Expected behavior

The skill should not guess. It should ask for the smallest missing artifacts first, such as:

- the Service manifest
- the backing Pod or Deployment labels
- the namespace
- current endpoints output
- any relevant Ingress or NetworkPolicy if traffic is involved
- any relevant `ResourceQuota`, `LimitRange`, or Pod Security context if admission or scheduling is failing
