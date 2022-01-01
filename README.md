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
 
$minikube get svc [service_name_to_expose]
$minikube kubectl edit service/[service_name_to_expose]

search for "type: ClusterIP" under Spefication label then replace it with "type: NodePort" & save

   $minikube service prometheus-alertmanager
so I reccomend to expose your service using service.yaml file like this:
|-----------|-------------------------|-------------|-----------------------------|
| NAMESPACE |          NAME           | TARGET PORT |             URL             |
|-----------|-------------------------|-------------|-----------------------------|
| default   | prometheus-alertmanager | http/80     | http://192.168.59.100:30534 |
|-----------|-------------------------|-------------|-----------------------------|
* Ouverture du service default/prometheus-alertmanager dans le navigateur par défaut...


3-Make promtheus as data source in Grafana:
  ![image](https://user-images.githubusercontent.com/74049018/147853040-4fc4eef4-cf4d-4c75-b91e-5bcaa26f3cd2.png)
  
4-upload a ready to use dashboard template from :
   https://grafana.com/grafana/dashboards/
   
5-Configure Alerting to better monitor your K8s :
  a- choose create alert rule from this panel 
  <img width="737" alt="ca" src="https://user-images.githubusercontent.com/74049018/147853457-12c7e34a-d551-4f84-a427-81428cdf72e4.PNG">
  
  b-![image](https://user-images.githubusercontent.com/74049018/147853537-e79628f9-6000-4034-b450-0e39ff66df2d.png)
  c-![image](https://user-images.githubusercontent.com/74049018/147853547-9a902af8-057e-4d28-9ec4-0d34922abb6a.png)
  d-![image](https://user-images.githubusercontent.com/74049018/147853562-49b720f9-d01f-4186-96d9-cfd650181fdb.png)
  e-![image](https://user-images.githubusercontent.com/74049018/147853572-b47b503c-2882-41de-9af4-ca84d9499929.png)
  f-![image](https://user-images.githubusercontent.com/74049018/147853583-f23239df-0d13-483d-96a0-f26548fbda41.png)
  g-![image](https://user-images.githubusercontent.com/74049018/147853604-73cdc5c4-8367-49e8-ba00-ebcd0abe7f9e.png)
  h-![image](https://user-images.githubusercontent.com/74049018/147853617-a15ed8dd-b9f8-48ff-a7cf-f8ca13ae9f55.png)
  
  then you will be notified via the notification channel you already configured . or you could c ur alert via the folder in alertin:
  ![image](https://user-images.githubusercontent.com/74049018/147853726-0ce806ae-5430-46fb-a823-273de848760b.png)


 hope you  enjoy it ;)









