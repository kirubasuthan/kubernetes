# Kubernetes Manifests for Jenkins Deployment

Refer https://devopscube.com/setup-jenkins-on-kubernetes-cluster/ for step by step process to use these manifests.

### Steps to setup

#### Create NameSpace for Jenkins 
`kubectl create namespace devops-tools`

#### Create Service Account
`kubectl apply -f serviceAccount.yaml`

#### Switch to devops-tools namespace (Not mandatory. But useful to run commands directly in the new namespace)
`kubectl config set-context --current --namespace devops-tools`

#### Create Persistent Volume, Persistent Volume Claim 
`kubectl apply -f volume.yaml`

#### Create Deployment
`kubectl apply -f deployment.yaml`

#### Create Service
`kubectl apply -f service.yaml` 
`Note: The service has to be of type LoadBalancer instead of NodePort. Only LoadBalancer will bind the service external IP to localhost. NodePort to be used in the actual cluster`

### Access Jenkins 
At `http://localhost:8080`

### Get Jenkins Initial Admin Password
`kubectl exec -it jenkins-559d8cd85c-cfcgk cat /var/jenkins_home/secrets/initialAdminPassword -n devops-tools` 


