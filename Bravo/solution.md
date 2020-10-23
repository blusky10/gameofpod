## drpal-pv-hostpath, drupal-mysql-pv-hostpath

> /drupal-mysql-data (create the directory on Worker Nodes)  
/drupal-data (create the directory on Worker Nodes)

  * connect node01 : ssh node01
  * mkdir /drupal-mysql-data
  * mkdir /drupal-data

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
