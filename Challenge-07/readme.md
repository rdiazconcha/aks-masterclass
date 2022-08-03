# Challenge 07 - Labels and Selectors
## Estimated time to complete: 20 minutes

## Directions
1. Describe an existing Pod, Deployment, or Service in your cluster.  Inspect their current labels.
2. Create a new Deployment file that includes a Pod template with different labels and uses a complex selector filtering.  Refer to the following code snippet

```
apiVersion: apps/v1
kind: Deployment
spec:
  selector:
    matchLabels:
      app: myapp
    matchExpressions:
      - {key: tier, operator: In, values: [cache]}
      - {key: env, operator: NotIn, values: [dev]}
…
```


## Questions
1. What happens if you deploy an isolated Pod with the same labels that match with the selector?
2. Discuss: What are the recommended labels? Why?