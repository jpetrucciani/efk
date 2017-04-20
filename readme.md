cd k8s/efk
kubectl create -f fluentd.yaml
kubectl create -f elasticsearch.yaml
kubectl create -f kibana.yaml
# wait 10 min
# make a htpasswd for auth on your local system, mine's at /etc/nginx/.htpasswd
kubectl --namespace=kube-system create secret generic htpasswd --from-file=/etc/nginx/.htpasswd
kubectl create -f kibana-proxy.yaml


now you should have a kube kibana elb in ec2