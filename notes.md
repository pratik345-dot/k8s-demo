kubectl config set-context --current --namespace=<desired-namespace>
kubectl api-resources | grep pods

kubectl create namespace demo
kubectl delete namespace demo

kubectl get po -n=demo -w  
kubectl inspect pod <name>
kubect describe pod <name>
kubectl logs --tail=100 -n demo-app po/mongo-1 or -f
kubectl logs -n demo-app po/mongo-1 -f

kubectl rollout status deployment/<name>
kubectl rollout history deployment/<name>
kubectl rollout undo deployment/<name> --to-revision=1
 
kubectl get endpoints -n demo-app
kubectl descirbe service <name> -n demo-app
kubectl get service -n demo-app -o wide

kubectl port-forward service/user-service -n demo-app 3005:3000
kubectl describe hpa user-service-hpa -n demo-app

minikube addons enable metrics-server
autocannon -c 100 -d 30 http://localhost:3005/hello
curl -X POST http://localhost:3005/add -H "Content-Type: application/json" -d '{"name":"Alice"}'

argocd admin dashboard -n argocd
argocd login localhost:8080 --username admin --password $(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d)


kubectl config get-contexts
kubectl config current-context