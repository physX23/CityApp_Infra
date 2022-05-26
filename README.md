# CityApp_Infra
## Infra manifests for deploying city-app
1. Create minikube cluster
```
minikube start
```
2. Create mysql database
```
docker run --name=mysql --restart on-failure -d mysql/mysql-server:latest
```
3. Create db and table
```
CREATE DATABASE mytestdb;
CREATE TABLE `cities` (   
`id` int(6) unsigned NOT NULL AUTO_INCREMENT,
`city` varchar(30) NOT NULL,
PRIMARY KEY (`id`) ) ENGINE=InnoDB;
```
4. Turn on addon
```
minikube addons enable ingress
```
5. Deploy app.yaml & ingress.yaml
```
kubectl -f app.yaml,ingress.yaml
```
6. You can use HPA for high-availability your app
```
kubectl autoscale deployment city-app --cpu-percent=70 --min=1 --max=5
```
