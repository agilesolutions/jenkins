# Official Jenkins HELM distribution

* helm fetch --untar stable/jenkins
* helm install --name jenkins --namespace jenkins .
* Get your 'admin' user password by running
* printf $(kubectl get secret --namespace jenkins jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
* Get the Jenkins URL to visit by running these commands in the same shell: NOTE: It may take a few minutes for the LoadBalancer IP to be available. You can watch the status of by running 'kubectl get svc --namespace jenkins -w jenkins' 
* export SERVICE_IP=$(kubectl get svc --namespace jenkins jenkins --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}") 
* echo http://$SERVICE_IP:8080/login
* Login with the password from previous steps and the username: admin
* kubectl describe svc -n jenkins jenkins

## create volume and claim

* create -f  jenkins-hostpath.yaml
* kubectl create -f  jenkins-pvc.yaml
* helm install --name my-release --set persistence.existingClaim=jenkins-pvc stable/jenkins
* [read](https://8gwifi.org/docs/kube-jenkins.jsp)


## Install on Katacoda HELM instruction page and have fun

[Katacoda helm package manager](https://www.katacoda.com/courses/kubernetes/helm-package-manager)

## install HELM

* curl -LO https://storage.googleapis.com/kubernetes-helm/helm-v2.8.2-linux-amd64.tar.gz
* tar -xvf helm-v2.8.2-linux-amd64.tar.gz
* mv linux-amd64/helm /usr/local/bin/
* helm init
* helm repo update