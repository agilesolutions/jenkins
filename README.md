# Official Jenkins HELM distribution

* helm fetch --untar stable/jenkins
* cp values.yaml /springboot-helm-kubernetes/jenkins/myvalues.yaml
* vim  /springboot-helm-kubernetes/jenkins/myvalues.yaml
* helm install --name jenkins--values myvalues.yaml --namespace jenkins. --dry-run
* helm install --name jenkins--values myvalues.yaml --namespace jenkins .
* Get your 'admin' user password by running
* printf $(kubectl get secret --namespace jenkins jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
* Get the Jenkins URL to visit by running these commands in the same shell: NOTE: It may take a few minutes for the LoadBalancer IP to be available. You can watch the status of by running 'kubectl get svc --namespace jenkins -w jenkins' export SERVICE_IP=$(kubectl get svc --namespace jenkins jenkins --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}") echo http://$SERVICE_IP:8080/login
* Login with the password from previous steps and the username: admin

## Install on Katacoda HELM instruction page and have fun

[Katacoda helm package manager](https://www.katacoda.com/courses/kubernetes/helm-package-manager)