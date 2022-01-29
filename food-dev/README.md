# Simple kubernetes Deployment for my food-site

Kubernetes is a container orchestration platform used to orchestrate and manage containers.

I created a deployment object file for my beans and rice site.

For the beans deployment file(beans-deployment.yaml), i scaled up to 2 replicas and exposed containerPort 9000 
For the beans service file, i used NodePort to expose the pods to the outside world.

For the rice deployment object file(rice-deployment.yaml), i scaled up to 2 replicas and exposed containerPort 8000
for the rice service file, i used NodePort to expose the pods to the outside world.

to start both deployments and service:
kubectl apply -f .

To check if the deployments, pods, services and replicas are ready:
kubectl get all -o wide

To check the host IP, there are several methods to do these, either:
kubectl exec -it <pod-name> sh
or
kubectl get <pod-name> -o yaml 
then search for hostIP, that's the ip address of the node the pod is on.

To be able to access the beans and rice deployment on your local machine, get the port from the beans and rice service, it's usually between 30000-32767
then access each deployment using the hostIP:port.
assuming hostIP for beans pod is 192.168.0.2 and the port for beans service is 32500

you can access the beans page online by pressing this on your browser:
192.168.0.2:32500

and the page comes up.


