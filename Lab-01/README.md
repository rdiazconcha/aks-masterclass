# Lab 01 - Your First Pod
## Estimated time to complete: 20 minutes

We're going to run our first container on Kubernetes.


Step 0: Ensure Kubernetes is running
------------------------------------

1. Run `kubectl cluster-info` and `kubectl version`.


Step 0: Build the image
-----------------------

For this exercise, we're going to be using the `hellonode:0.1` image built in the previous course (Lab 03).  If you don't have it, you can use `rdiazconcha/hellonode:0.1` as the container image.


Step 1: Craft a pod.yaml file
-----------------------------

In general we won't craft pods directly.  Rather we'll build pods as part of a deployment.  Let's get familiar with what is a pod so when we build a deployment these concepts make sense.

**Note:** Yaml files are white-space significant.  Indenting is done with **2 spaces**, not 4 spaces, not tabs.

Each Kubernetes object has an `apiVersion`, a `kind`, a `metadata` section, and a `spec` section that holds the details.

1. Create a new file in this `start` directory named `pod.yaml`

2. Write these lines:

   ```
   apiVersion: v1
   kind: Pod
   ```

   This says we're using a `Pod` object, and it's found in Kubernetes's `v1` namespace.

3. Write these lines:

   ```
   metadata:
     name: hellonode
   ```

   With this, we've named the pod `hellonode`.

4. Add these lines to the `metadata` section:

   ```
     labels:
       app: hellonode
       version: v0.1
   ```

   We're giving Kubernetes a bit of metadata about the pod -- a list of arbitrary name-value pairs.  We could put anything we wanted here -- service tags, environment name, your favorite color.

   We'll use these when we discuss service's selectors.

   **Note:** both the name and the value must be strings, so ~~`version: 0.1`~~ is invalid, but `version: '0.1'` is ok.  In this case we use `version: v0.1` to ensure it's a string without needing quotes.

5. The next section is the details about the pod -- the container(s) in it:

   ```
   spec:
     containers:
   ```

6. We only have a single container, let's specify the container details:

   ```
     - name: hellonode
   ```

   The first `-` creates a new entry in the containers array and begins the object that describes this container.  We then name the container `hellonode`.

7. Let's add the image Kubernetes should pull from Docker Hub:

   ```
       image: [REPOSITORY]/hellonode:0.1
   ```
   
   > Replace [REPOSITORY] with the name of your Docker Hub repository.

   We don't start this line with a dash because it's part of the object definition that defines this pod.  (Yeah, yaml is weird.)

   Good thing we built this image previously.  Kubernetes won't need to pull it because it already exists.  However, it must exist in your Docker Hub repository.

8. Add the port details:

   ```
       ports:
       - containerPort: 3000
   ```

9. For reference, here's our completed container details:

   ```
   spec:
     containers:
     - name: hellonode
       image: [REPOSITORY]/hellonode:0.1
       ports:
       - containerPort: 3000
   ```

10. Save the pod.yaml file.


Step 2: Schedule the pod
------------------------

1. Open a command prompt in this directory, and run:

   ```
   kubectl apply -f pod.yaml
   ```

   This says "please schedule the thing I've got in the yaml file `pod.yaml`.

2. Run this command:

   ```
   kubectl get pods
   ```

   Do you see your pod?  Is it running?

3. Run this command:

   ```
   kubectl describe pods hellonode
   ```

   This command tells us a lot about the pod.

4. Run this command:

   ```
   kubectl port-forward pods/hellonode 3000:3000
   ```

   This command won't end.  It sets up a proxy so you can browse to the pod.  This is generally not a good idea, but we're experimenting.

5. Open a browser to [http://localhost:3000/](http://localhost:3000/).  Do you see the site?

6. Hit `Cntrl` + `C` to break out of the port-forward command.  You can check `kubectl get pods` to see the pod is still running.

7. Run this from the terminal:

   ```
   kubectl delete -f pod.yaml
   ```

   We just scheduled Kubernetes to delete this pod.  It'll terminate the container running in it.

8. If you hurry, you can see the pod terminating:

   ```
   kubectl get pods
   ```
