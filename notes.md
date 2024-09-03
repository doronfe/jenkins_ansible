September 3rd, 2024 course notes:
back after vacation.

include in each task: readme, contibuters, install

------------------------
Links:
roadmap.sh

howtoforge.com - tutorials

linux-training.be
------------------------
deployment:
tragedy of systemd - youtube video
systemctl - service management
".service" file, /etc/systemd/system

deploying microservices presentation ...

kubernetes concepts:

pod - smallest resource in k8s, yaml, should run one container as best practice (you can run more)
the pod gets a dynamic name
replica set - replica of the pod, it is "down" by default and will be "up" if the pod crashes

deployment has pods and replica sets.


service - connects the deployment with the internet

ingress - Ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster. Traffic routing is controlled by rules defined on the Ingress resource.

egress - 

storage class:
pv - persistent volume, application data
pvc - persistent volume claim, 

stateful set: has the storage inside the container
StatefulSet is the workload API object used to manage stateful applications.

Manages the deployment and scaling of a set of Pods, and provides guarantees about the ordering and uniqueness of these Pods.

install k3s:
curl -L get.k3s.io | sh - 
if you get warning in "kubectl get nodes" run: curl -L get.k3s.io | sh - K3S_KUBECONFIG_MODE="644" sh -


k3s commands:
kubectl get nodes
ls -l /etc/rancher/k3s/k3s.yaml 

gedit /etc/systemd/system/k3s.service

generate k3s yaml:
kubectl create deployment <name> 
kubectl create deployment nginx --image=nginx:latest

create with yaml:
kubectl create deployment nginx --image=nginx:latest -o yaml

output:
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: "2024-09-03T17:18:46Z"
  generation: 1
  labels:
    app: nginx
  name: nginx
  namespace: default
  resourceVersion: "2413"
  uid: 24fcbc21-4744-4318-9eb5-c2f58cd5060a
spec:
  progressDeadlineSeconds: 600
  replicas: 1
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: nginx
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: nginx
    spec:
      containers:
      - image: nginx:latest
        imagePullPolicy: Always
        name: nginx
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      dnsPolicy: ClusterFirst
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext: {}
      terminationGracePeriodSeconds: 30
status: {}


https://kubernetes.io/docs/concepts/workloads/controllers/deployment/


kubectl get deployment - (wait until it's 1/1 - it will start as 0/1)

source <(kubectl completion bash)



kubectl get pods
notice that the pod get a random number.
output:
NAME                     READY   STATUS    RESTARTS   AGE
nginx-7584b6f84c-hzhd4   1/1     Running   0          16m


kubectl describe deployments nginx

kubectl describe pods nginx

kubectl delete deployment nginx

kubectl apply -f nginx.yaml






kubectl create deployment nginx --image=nginx:latest
kubectl create service clusterip nginx --tcp=80:8080

debugging can be done via "describe"



