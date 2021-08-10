# springboot-docker
 
 
## Step 1 - Create a new naespace  
``` 
$ oc new-project spring-boot-docker
```


## Step 2 - Create a new project 
``` 
$ oc new-app --docker-image gazgeek/springboot-helloworld --name spring-boot-docker

example output:

--> Found container image b538dc3 (6 years old) from Docker Hub for "gazgeek/springboot-helloworld"

    * An image stream tag will be created as "spring-boot-docker:latest" that will track this image

--> Creating resources ...
    imagestream.image.openshift.io "spring-boot-docker" created
    deployment.apps "spring-boot-docker" created
    service "spring-boot-docker" created
--> Success
    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
     'oc expose service/spring-boot-docker' 
    Run 'oc status' to view your app.
```  


## step 3 - Check to see if your application is running
```
$ oc get pods

example output:

NAME                                 READY   STATUS    RESTARTS   AGE
spring-boot-docker-7bcc97cb5-hdvj9   1/1     Running   0          5s
```

## step 4 - Get the service and then expose it
```
$ oc get svc
NAME                 TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE
spring-boot-docker   ClusterIP   xxx.xx.xx.xx   <none>        8080/TCP   12s

$ oc expose svc/spring-boot-docker
route.route.openshift.io/spring-boot-docker exposed
```

## step 5 - Check to see if your application is running
```
$ oc get route 
NAME                 HOST/PORT                                                            PATH   SERVICES             PORT       TERMINATION   WILDCARD
spring-boot-docker   spring-boot-docker-spring-boot-docker.xxxxx        spring-boot-docker   8080-tcp                 None
