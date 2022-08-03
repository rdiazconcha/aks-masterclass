# Challenge 09 - Rolling updates
## Estimated time to complete: 20 minutes

## Directions
1. Describe an existing Deployment.  If you don't have one, create it.
2. Get and describe the existing Pods.
3. Modify the spec element of the Deployment's Pod template.  You can use `kubectl set image`, `kubectl edit`, or `kubectl apply`.
4. Get and describe the existing Pods.  What is happening?
5. Display the status of the rollout.
6. Modify again the spec element of the Deployment's Pod template.  This time, change the container image to something purposefully wrong.
7. Get and describe the existing Pods.  What is happening?
8. Display the status of the rollout.
9. Rollback the deployment.
10. Get and describe the existing Pods.  What is happening?

## Questions
1. What is the difference between Deployment and ReplicaSet?
2. Is modifying the container image with `kubectl set image` a good rollout strategy for your organization?  Why?
3. Discuss: How can you incorporate the Rolling updates feature into your existing development workflow?