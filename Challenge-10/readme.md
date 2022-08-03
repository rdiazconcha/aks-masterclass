# Challenge 10 - Health checks
## Estimated time to complete: 30 minutes

## Directions
1. Create a liveness probe in a Deployment's Pod template.  Use both command execution and HTTP GET request probing mechanisms.
2. Get and describe the Pods immediately, and after a while.  What happens?

```
spec:
  containers:
  - name: liveness
    image: k8s.gcr.io/busybox
    args:
    - /bin/sh
    - -c
    - touch /tmp/healthy; sleep 30; rm -f /tmp/healthy; sleep 600
    livenessProbe:
      exec:
        command:
        - cat
        - /tmp/healthy
      initialDelaySeconds: 5
      periodSeconds: 5
```

```
spec:
  containers:
  - name: liveness
    image: k8s.gcr.io/liveness
    args:
    - /server
    livenessProbe:
      httpGet:
        path: /healthz
        port: 8080
        httpHeaders:
        - name: Custom-Header
          value: Awesome
      initialDelaySeconds: 3
      periodSeconds: 3
```

## Questions
1. What is the difference between Liveness, Readiness, and Startup probes?
2. What would be a good option for container applications that require external systems or services?  Why?

## Bonus
1. Create a readiness and startup probes.
1. Create an ASP.NET Core Web API project that exposes a /liveness endpoint and containerize it.  Use the HTTP GET request probing mechanism in your Pod template.