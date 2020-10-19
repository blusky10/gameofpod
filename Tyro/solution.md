## admin
Certificate and key pair for user drogo is created under /root. Add this user to kubeconfig = /root/.kube/config, User = drogo, client-key = /root/drogo.key client-certificate = /root/drogo.crt
Create a new context in the default config file (/root/.kube/config) called 'developer' with user = drogo and cluster = kubernetes

kubectl config set-credentials drogo --client-key=/root/drogo.key --client-certificate=/root/drogo.crt
kubectl config set-context developer --cluster=kubernetes --user=drogo

## change context
set context 'developer' with user = 'drogo' and cluster = 'kubernetes' as the current context.
kubectl config use-context developer

## solutions
Zyhys perzys stepagon schedulara Oño resarc, se poda lys qelitsos sikagon