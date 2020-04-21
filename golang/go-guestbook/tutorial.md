# Go Guestbook Application #

## Introduction ##

Welcome to the Go Guestbook sample application for GCP!

This example shows how to build a simple multi-tier web application using
Kubernetes and Docker. The application consists of a web front end, a backend, and a MongoDB database.

### Opening Application Workspace ###

Before we begin, let's open the IDE workspace to focus on the Go Guestbook sample applicationL

* Navigate to the <walkthrough-editor-spotlight spotlightId="fileMenu">File</walkthrough-editor-spotlight> menu and select **Open Workspace...**
* Select **`cloudshell_open/cloud-code-samples/golang/go-guestbook`**
* Click **Open**


## Code Tour ##

This sample is structured the way we recommend structuring an applications in Cloud Code.

**`kubernetes-manifests/`** folder contains pod specification for the application nodes:
* <walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/kubernetes-manifests/guestbook-frontend.deployment.yaml">guestbook-frontend.deployment.yaml</walkthrough-editor-open-file> - frontend node spec
* <walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/kubernetes-manifests/guestbook-backend.deployment.yaml">guestbook-backend.deployment.yaml</walkthrough-editor-open-file> - backend node spec
* <walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/kubernetes-manifests/guestbook-mongodb.deployment.yaml">guestbook-mongodb.deployment.yaml</walkthrough-editor-open-file> - database node spec

**`src/`** folder contains pod specification for the application nodes:

* frontend/ contains web server logic (<walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/src/frontend/main.go">main.go</walkthrough-editor-open-file>)
and the accompanying <walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/src/frontend/Dockerfile">Dockerfile</walkthrough-editor-open-file> 
* backend/ contains API server logic (<walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/src/backend/main.go">main.go</walkthrough-editor-open-file>)
and the accompanying <walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/src/backend/Dockerfile">Dockerfile</walkthrough-editor-open-file> 

### Configuration files ###

* <walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/skaffold.yaml">skaffold.yaml</walkthrough-editor-open-file> is the config file for Skaffold, which is used by Cloud Code to build and run images
* <walkthrough-editor-open-file filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/.vscode/launch.json">.vscode/launch.json</walkthrough-editor-open-file> contains application configuration for Cloud Code
  * <walkthrough-editor-select-line filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/.vscode/launch.json" startLine="4" endLine="12" startCharacterOffset="0" endCharacterOffset="0">run on Kubernetes</walkthrough-editor-select-line>
  * <walkthrough-editor-select-line filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/.vscode/launch.json" startLine="14" endLine="25" startCharacterOffset="0" endCharacterOffset="0">debug frontend on Kubernetes</walkthrough-editor-select-line>
  * <walkthrough-editor-select-line filePath="cloudshell_open/cloud-code-samples/golang/go-guestbook/.vscode/launch.json" startLine="27" endLine="38" startCharacterOffset="0" endCharacterOffset="0">debug backend on Kubernetes</walkthrough-editor-select-line>

## Creating a Google Kubernetes Engine cluster ##

To create a GKE cluster where you can run your guestbook application, follow these steps
* Navigate to the Google Kubernetes Engine explorer using the Cloud Code view, by clicking its <walkthrough-editor-spotlight spotlightId="fileMenu">icon in the left activity bar</walkthrough-editor-spotlight>
* Click the '+' button to create a new GKE cluster
* Fill out fields in the Create Cluster wizard and click 'Create Cluster'.


## Running Go Guestbook Application ##

To run your application, you'll need the Cloud Code: Run on Kubernetes command.

* Choose the Run on Kubernetes command using the Cloud Code status bar.
* Confirm whether you'd like to use the current cluster context to run the app in (or switch to a preferred one).
* Depending on the context chosen, you may be prompted to choose an image registry to push the images to. This choice is stored in in your launch configuration (found in .vscode/launch.json)
* Cloud Code then builds your containers, pushes them to the registry, applies Kubernetes configurations to the cluster, and returns the IP address you can use to browse your live application.

## Viewing Logs ##

To help with troubleshooting problems with your app, you can see the logs from your running pods using the Log Viewer that comes integrated with Cloud Shell. To view logs, follow these steps:
* Launch the Log Viewer by typing **Cloud Code: View Logs** using the Command Pallete (accessible with **Ctrl/Cmd+Shift+P**)
* Search for the running app, in this case 'go-guestbook', to view logs from using the deployment field in the Log Viewer search box.

## Conclusion

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

Congratulations! You've just created and run your first Kubernetes app on GKE.

<walkthrough-inline-feedback></walkthrough-inline-feedback>

