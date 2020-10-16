## jekyll-pv

## jekyll-pvc

## jekyll

## jekyll-node-service

## kube-config
set context 'developer' with user = 'drogo' and cluster = 'kubernetes' as the current context.

~/.kube/config

- conext:
    cluster: kubernetes
    user: drogo
  name: developer

current-context: developer
users:
- name: drogo

## developer-role
'developer-role', should have all(*) permissions for services in development namespace
'developer-role', should have all permissions(*) for persistentvolumeclaims in development namespace
'developer-role', should have all(*) permissions for pods in development namespace
## developer-rolebinding
create rolebinding = developer-rolebinding, role= 'developer-role', namespace = development
rolebinding = developer-rolebinding associated with user = 'drogo'

## admin
Certificate and key pair for user drogo is created under /root. Add this user to kubeconfig = /root/.kube/config, User = drogo, client-key = /root/drogo.key client-certificate = /root/drogo.crt
Create a new context in the default config file (/root/.kube/config) called 'developer' with user = drogo and cluster = kubernetes

kubectl config set-credentials drogo --client-key=/root/drogo.key --client-certificate=/root/drogo.crt --embed-certs