# spark-at-scale
Spark Kubernetes Containerization

## prerequisite
- Provisioned Kubernetes Cluster using Terrafrom or other provisioning tool 
- Depoyed Kubernetes Cluster on AWS, GCP, Azure, Digital Ocean, Openshift, Rancher or On-Prime 
- Configured Controlplane, Agents and Networks

### Create namespace, service-account and roles-rolebindings for spark cluster

### Namespace and role-rolebindings
$ kubectl create -f namespace spark
$ kubectl create serviceaccount spark

$ kubectl create clusterrolebinding spark-role --clusterrole=edit --serviceaccount=default:spark --namespace=default


### Configuration and service definition
$ kubectl create -f spark-configuration-configmap.yaml
$ kubectl create -f jobmanager-service.yaml

### Create the deployments for the cluster
$ kubectl create -f jobmanager-session-deployment-non-ha.yaml
$ kubectl create -f taskmanager-session-deployment.yaml