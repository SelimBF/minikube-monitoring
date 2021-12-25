minikube-monitoring

This is a full monitoring lab for minikube cluster 
it's a step by step guide to monitor Minikube cluster using Prometheus,Grafana,AlertManager,Pushgateway

0- Requirements:

* Minikube : you could install Minikube directly from : https://minikube.sigs.k8s.io/docs/start/
* helm :     you could install Minikube directly from : https://get.helm.sh/helm-canary-windows-amd64.zip


1-installation 

 a-to deploy your first cluster open cmd then type:
  $Minikube start 

 b-Installing Prometheus using helm which need to be launched from cmd using path/helm.exe (in windows case) then:
  $helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
  $helm install prometheus prometheus-community/prometheus

 c- Installing Grafana using helm
  $helm repo add grafana https://grafana.github.io/helm-charts
  $helm install grafana grafana/grafana

 d-check your pods & service  are running fine :
  $minikube kubectl get pods
  $minikube kubectl get svc

2-Exposing service : 
  #export POD_NAME=$(kubectl get pods --namespace default -l "app=prometheus,component=server" -o jsonpath="{.items[0].metadata.name}")
   kubectl --namespace default port-forward $POD_NAME 9090"

Note: this cmd will not work in K8s version 1.22.4 +

so I reccomend to expose your service using service.yaml file like this:

$minikube get svc [service_name_to_expose]
$minikube kubectl edit service/[service_name_to_expose]

search for "type: ClusterIP" under Spefication label then replace it with "type: NodePort" & save

then type :


$minikube service prometheus-alertmanager

|-----------|-------------------------|-------------|-----------------------------|
| NAMESPACE |          NAME           | TARGET PORT |             URL             |
|-----------|-------------------------|-------------|-----------------------------|
| default   | prometheus-alertmanager | http/80     | http://192.168.59.100:30534 |
|-----------|-------------------------|-------------|-----------------------------|
* Ouverture du service default/prometheus-alertmanager dans le navigateur par défaut...

This take me 20 days to resolve exposing under 1.22.4  hope you  enjoy it ;)









