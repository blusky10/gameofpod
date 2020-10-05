Master node: coredns deployment has image: 'k8s.gcr.io/coredns:1.3.1'
Fix kube-apiserver. Make sure its running and healthy.
kubeconfig = /root/.kube/config, User = 'kubernetes-admin' Cluster: Server Port = '6443'


1. 
kubectl get nodes
> X509.XXX 에러

docker ps | grep api
docker container logs [containder id]

/etc/kubernetes/manifests/kube-apiserver.yaml

- --client-ca-file= 파일 경로 변경
- --client-ca-file=/etc/kubernetes/pki/ca.crt

2. vi ~/.kube/config
cluser port -> 6443

3. kubectl edit deployment coredns
image 변경 



node01 is ready and can schedule pods?

1. kubectl uncordon node01

