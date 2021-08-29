# Espace-CD
This is a sample repository to cover the continous-deployment of the app using helm chart.

# User workflow
1. Developer will make a check in the branch by changing the values in the values.yaml file under espace chart.
2. Jenkins will automatically trigger the change and deploy the app with image specified in the given namespace.

# Our deployment
1. In this workflow:
    * for app-ver1: We will use the image bibhav2937/espace:v1. We will be changing the value of image key in values.yaml to bibhav2937/espace and tag to v1.
    * for app-ver2: We will use the image bibhav2937/espace:v2. We will be changing the value of image key in values.yaml to bibhav2937/espace and tag to v2.
2. Namespace used for the deployment is espace.
3. Deployment occurs from espacecd branch.
4. Apps are exposed using clusterIp in the cluster.

# Verification
1. Successful deployment can be verified by port-forwarding the service exposed by the deployment and sending traffic to it from the browser.
2. Command: kubectl port-forward service/SERVICE_NAME -p LOCAL_PORT:SERVICE_PORT -n NAMESPACE

