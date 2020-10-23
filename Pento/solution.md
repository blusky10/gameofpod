## master-node
> Master node: coredns deployment has image: 'k8s.gcr.io/coredns:1.3.1'  
Fix kube-apiserver. Make sure its running and healthy.  
kubeconfig = /root/.kube/config, User = 'kubernetes-admin' Cluster: Server Port = '6443'

- ca-file 경로 변경
  
  /etc/kubernetes/manifests/kube-apiserver.yaml

  kube-apiserver.yaml 파일의 --client-ca-file 을 변경해준다.

  변경전 : --client-ca-file=/etc/kubernetes/pki/ca-authority.crt

  변경후 : --client-ca-file=/etc/kubernetes/pki/ca.crt

- ~/.kube/config 변경

  cluster port 를 6443 으로 변경한다.

  변경전 : server: https://172.17.0.28:2379

  변경후 : server: https://172.17.0.28:6443

- coredns Deployment 의 이미지를 변경한다. 
  ```
  kubectl edit deployment coredns
  ```

## node01
> node01 is ready and can schedule pods?  

- uncordon 명령어 실행
  ```
  kubectl uncordon node01
  ```

## web
> node01 has hostPath created = '/web'  

  * connect node01 : ssh node01
  * mkdir /web


## 리소스 생성은 다음 yaml 파일 참조
    data-pv.yaml
    data-pvc.yaml
    gop-file-server.yaml
    gop-fs-service.yaml