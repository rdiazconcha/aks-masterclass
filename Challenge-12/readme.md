# Challenge 12 - Secrets
## Estimated time to complete: 20 minutes

## Directions
1. Create a new Secret object
2. Use it in the environment variables of the Deployment's Pod template.  Refer to the following code snippet:

```
 env:
   - name: CONN_STRING
     valueFrom:
       secretKeyRef:
         name: mysecret
         key: connstring
```
3. Get and describe all the secrets

## Questions
1. Discuss: What would be a good way to use Secret objects in your projects?  Are there currently better choices in your organization?

## Bonus
1. Create an ASP.NET Core Web app project that displays the value of environment variables.  Test with different Secret values.