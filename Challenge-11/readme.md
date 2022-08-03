# Challenge 11 - ConfigMaps
## Estimated time to complete: 20 minutes

## Directions
1. Create a new ConfigMap object
2. Use it in the environment variables of the Deployment's Pod template.  Refer to the following code snippet:

```
 env:
   - name: YOUR-ENVIRONMENT-VARIABLE
     valueFrom:
       configMapKeyRef:
         name: THE-CONFIGMAP
         key: THE-KEY
```
3. Get and describe all the ConfigMaps

## Questions
1. Discuss: What would be a good way to use ConfigMap objects in your projects?

## Bonus
1. Create an ASP.NET Core Web app project that displays the value of environment variables.  Modify the values of the ConfigMap.