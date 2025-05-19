DevOps Task 5: 
Build a Kubernetes Cluster Locally with Minikube

Objective:
Deploy and manage a simple NGINX application in a local Kubernetes cluster using Minikube

Tools Used
•	Minikube
•	kubectl
•	Docker
•	Windows PowerShell

Step-by-Step Execution

1.Start Minikube

minikube start

2. Create Deployment

kubectl apply -f mydeployment.yaml

 3. Expose Service via NodePort

kubectl apply -f service.yaml

 4. Check Pods

kubectl get pods

5. Check Services

kubectl get svc

6. Access App in Browser

minikube service nginx-service

7. Verify Running Pods & Services

kubectl get pods

kubectl get services

8. Scale the Deployment

kubectl scale deployment my-app-deployment --replicas=4

kubectl get pods

9. Inspect Pod Details and Logs

kubectl describe pod <pod-name>

kubectl logs <pod-name>


YAML Files

1.	mydeployment.yaml
yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80

2.	service.yaml
yaml 

apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30080

Outcome

By completing this task :
•	Learned Kubernetes basics: Pods, Deployments, Services
•	Practiced managing workloads via kubectl
•	Used Minikube to simulate a real Kubernetes environment
•	Exposed a deployed application using NodePort
•	Gained hands-on experience with basic kubectl commands for monitoring and scaling deployments

Task completed successfully and verified via browser access to running NGINX app.
