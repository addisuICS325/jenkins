#create namespace `jenkins`
    run kubectl apply jenkins\namespace.yaml
#In the namespace apply all yaml files
    kubectl -n jenkins apply -f .\jenkins
    deployment.apps/jenkins created
        deployment.apps/jenkins created
        service/jenkins created
        persistentvolume/jenkins created
        persistentvolumeclaim/jenkins-claim created
        serviceaccount/jenkins created
        clusterrole.rbac.authorization.k8s.io/jenkins created
        rolebinding.rbac.authorization.k8s.io/jenkins created
    kubectl -n jenkins get pods
    kubectl -n jenkins get service 
#Get the log for the pod and copy the admin password 
    kubectl -n jenkins logs <pods name ex "jenkins-b49c96f7d-lrsqx"> 
    jenkins-b49c96f7d-lrsqx
#Once we have admin pwd for jenkins, we will portforward to jenkins master 
    kubectl -n jenkins port-forward <pod name ex "jenkins-b49c96f7d-lrsqx"> 8080 
    then go to localhost to access jenkins 
    localhost:8080

After installing kubernetes-plugin for Jenkins

Go to Manage Jenkins | Bottom of Page | Cloud | Kubernetes (Add kubenretes cloud)
Fill out plugin values
Name: kubernetes
Kubernetes URL: https://kubernetes.default:443
Kubernetes Namespace: jenkins
Credentials | Add | Jenkins (Choose Kubernetes service account option & Global + Save)
Test Connection | Should be successful! If not, check RBAC permissions and fix it!
Jenkins URL: http://jenkins
Tunnel : jenkins:50000
Apply cap only on alive pods : yes!
Add Kubernetes Pod Template
Name: jenkins-slave
Namespace: jenkins
Service Account: jenkins
Labels: jenkins-slave (you will need to use this label on all jobs)
Containers | Add Template
Name: jnlp
Docker Image: aimvector/jenkins-slave
Command to run :
Arguments to pass to the command:
Allocate pseudo-TTY: yes
Add Volume
HostPath type
HostPath: /var/run/docker.sock
Mount Path: /var/run/docker.sock
Timeout in seconds for Jenkins connection: 300
Save