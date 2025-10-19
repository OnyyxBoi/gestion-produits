# Partie 1 :
### [URL de l'image](https://hub.docker.com/r/teoladouche/gp-php)
```
docker build -t teoladouche/gp-php:8.2-apache .\php/
```

### [URL de l'image](https://hub.docker.com/r/teoladouche/gp-mysql)
```
docker build -t teoladouche/gp-mysql:8.0 .\database\
```

# Partie 2 :
*Je dispose d'un alias me permettant d'appeller la commande **kubectl** par la commande **k***

```
> k apply -f .\minikube\
configmap/mysql-configmap created
deployment.apps/mysql created
persistentvolumeclaim/mysql-pvc created
service/db created
configmap/php-configmap created
deployment.apps/php-app created
service/php-service created

> k get po
NAME                       READY   STATUS    RESTARTS   AGE
mysql-7f9d4d9ff6-xtz8v     1/1     Running   0          62s
php-app-65ff979ccf-r5tdw   1/1     Running   0          62s

>  k get deploy
NAME      READY   UP-TO-DATE   AVAILABLE   AGE
mysql     1/1     1            1           7m21s
php-app   1/1     1            1           7m21s

> k get svc
NAME          TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
db            ClusterIP   10.99.115.65    <none>        3306/TCP       7m43s
kubernetes    ClusterIP   10.96.0.1       <none>        443/TCP        44d
php-service   NodePort    10.97.219.129   <none>        80:30080/TCP   7m43s
```

