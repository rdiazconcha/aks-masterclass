# Challenge 08 - Namespaces
## Estimated time to complete: 15 minutes

## Directions
1. Create a new namespace.  Refer to the following code snippet:

  ```
  apiVersion: v1
  kind: Namespace
  metadata:
    name:  THENAME
  ```
2. Deploy a new Deployment to this new namespace.
3. Configure your current kubectl context to use this new namespace (`kubectl config set-context`).
4. Get and describe the Deployment
5. Get and describe all the Pods
6. Configure your current kubectl context to use the default namespace.

## Questions
1. What do you have to to explore the objects in different namespaces?  Is there a better way?
2. Delete the new namespace that you created.  What happens?
3. Discuss: What would be a good namespace structure for your organization?