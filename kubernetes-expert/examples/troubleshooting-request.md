# Example: troubleshooting request

## Sample input

My pod is in `CrashLoopBackOff` after a new release.

```text
kubectl describe pod api-7c9bb4d4d5-6xsl8 -n demo

State:          Waiting
  Reason:       CrashLoopBackOff
Last State:     Terminated
  Reason:       Error
  Exit Code:    1
Events:
  Warning  Unhealthy  2m   kubelet  Liveness probe failed: Get "http://10.42.0.15:8080/health": dial tcp 10.42.0.15:8080: connect: connection refused
```

The app now listens on port 8443 and takes about 40 seconds to start.

## Expected behavior

- rank liveness and startup probe misconfiguration as a leading hypothesis
- explain why a startup probe may now be needed
- give a corrected probe example
- provide validation steps
