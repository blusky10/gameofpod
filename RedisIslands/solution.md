1. Make Directory in node
ssh node01
make /redis01~06

2. make pv
pv.yaml 참조

3. make statefulset
StatefulSet - Name: redis-cluster
Replicas: 6
Pods status: Running (All 6 replicas)
Image: redis:5.0.1-alpine
container name: redis, command: ["/conf/update-node.sh", "redis-server", "/conf/redis.conf"]
Env: name: 'POD_IP', valueFrom: 'fieldRef', fieldPath: 'status.podIP' (apiVersion: v1)
Ports - name: 'client', containerPort: '6379'
Ports - name: 'gossip', containerPort: '16379'
Volume Mount - name: 'conf', mountPath: '/conf', readOnly:'false' (ConfigMap Mount)
Volume Mount - name: 'conf', mountPath: '/conf', defaultMode = '0755' (ConfigMap Mount)
Volume Mount - name: 'data', mountPath: '/data', readOnly:'false' (volumeClaim)
volumes - name: 'conf', Type: 'ConfigMap', ConfigMap Name: 'redis-cluster-configmap',
volumeClaimTemplates - name: 'data'
volumeClaimTemplates - accessModes: 'ReadWriteOnce'
volumeClaimTemplates - Storage Request: '1Gi'

4. make config

Configure the Cluster. Once the StatefulSet has been deployed with 6 'Running' pods, run the below commands and type 'yes' when prompted.
Command: kubectl exec -it redis-cluster-0 -- redis-cli --cluster create --cluster-replicas 1 $(kubectl get pods -l app=redis-cluster -o jsonpath='{range.items[*]}{.status.podIP}:6379 ')

5. make service
Ports - service name 'redis-cluster-service', port name: 'client', port: '6379'
Ports - service name 'redis-cluster-service', port name: 'gossip', port: '16379'
Ports - service name 'redis-cluster-service', port name: 'client', targetPort: '6379'
Ports - service name 'redis-cluster-service', port name: 'gossip', targetPort: '16379'

6. Sīkudi nopāzmi! Valar dohaeris episierve!


## 리소스 생성은 다음 yaml 파일 참조
    drupal-mysql-pv.yaml
    drupal-mysql-pvc.yaml
    drupal-mysql-secret.yaml
    drupal-mysql.yaml
    drupal-mysql-service.yaml
    drupal-pv.yaml
    drupal-pvc.yaml
    drupal.yaml
    drupal-service.yaml