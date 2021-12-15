minikube kubectl get pods --l "app=prometheus,component=server" -o jsonpath="{.items[0].metadata.name}"
minikube kubectl get pods -l  -o jsonpath="{.items[0].metadata.name}"
minikube kubectl get pods 
minikube kubectl --namespace default port-forward $POD_NAME 9090
minikube kubectl default port-forward $POD_NAME 9090
minikube kubectl default port-forward 9090
minikube kubectl get namespaces
minikube kubectl default port-forward prometheus-server-bf5fffb66-jrb7
minikube kubectl default port-forward prometheus-server-bf5fffb66-jrb7 9090
minikube kubectl default --port-forward prometheus-server-bf5fffb66-jrb7 9090
export
minikube service prom-server
minikube service prometheus-server
minikube kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prom-server
minikube kubectl expose service prometheus-server type=NodePort --target-port=9090 --name=prom-server
minikube kubectl expose service prometheus-server type=NodePort target-port=9090 name=prom-server
minikube kubectl expose service prometheus-server type=NodePort 
minikube kubectl expose service prometheus-server --type=NodePort 
minikube kubectl version
minikube kubectl edit 
minikube kubectl edit deployment.yml
minikube kubectl get rsc
minikube kubectl get ressource
minikube kubectl get all
minikube kubectl edit service/prometheus-server
minikube kubectl get all
minikube service prom-server
minikube service prometheus-server
minikube ip
minikube dashboard
minikube kubectl get all
minikube kubectl edit service/prometheus-alertmanager
minikube service prometheus-alertmanager
minikube kubectl get svc -n default
minikube kubectl get svc  default
minikube kubectl get svc  
minikube service prometheus-alertmanager
minikube service prometheus-server
minikube kubectl get pods
minikube kubectl edit service/prometheus-alertmanager
minikube service prometheus-alertmanager
minikube kubectl get svc
minikube kubectl edit service/prometheus-pushgateway
minikube kubectl get svc
minikube service prometheus-pushgatwway
minikube service prometheus-pushgatway
minikube service prometheus-pushgateway
history
doskey /history
doskey /history > readme.txt
______________________________________________________________
lab guide :https://opensource.com/article/21/6/chaos-grafana-prometheus