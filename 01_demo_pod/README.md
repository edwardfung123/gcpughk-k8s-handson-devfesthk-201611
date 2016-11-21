A simple Pod demo.

# Files

`app.js` contains the simple nodejs application.

`Dockerfile` Well... the docker file...

`Makefile` contains a bunch of commands that no one will really remember
them... Feel free to copy and paste it into your projects....

`pod.yaml` is the config file for Kuberenetes. You can run `kubectl create -f pod.yaml` to create a pod.

# Workflow

`node app.js` to run the nodejs server locally. Then you might use the preview
function to test it if you are using google cloud shell.

Then, create the docker image with `make`.

Once the docker image is built, you can start a container with `make run`.
Again, you can use the preview function to connect to the container.

Since the image is stored in the local fs. We have upload the image to Google
Container Registry (GCR) in order to use it in our cluster.  Before that you
have to change the `PROJECT_ID` to your project's ID in `Makefile`.  Run `make
tag` to tag and upload the image.

Finally, we can create the pod. We change the `image` in `pod.yaml` to match
the GCR and tag in the `Makefile`. Then we can run `kubectl create -f pod.yaml`
to create the pod.

