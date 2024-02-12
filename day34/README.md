# Day 34 Task: Working with Services in Kubernetes

### Congratulation🎊 on your learning on Deployments in K8s on Day-33

## What are Services in K8s

In Kubernetes, Services are objects that provide stable network identities to Pods and abstract away the details of Pod IP addresses. Services allow Pods to receive traffic from other Pods, Services, and external clients.

## Task-1:

- Create a Service for your todo-app Deployment from Day-32
  <pre>
  kubectl create ns prod
  
  kubectl apply -f Deployment.yml -n prod

  kubectl expose deploy todo-app --type=NodePort --port=80 --target-port=8080 --name=day34 --namespace=prod --dry-run=client -o yaml >> serviceexpose.yml
  </pre>
- Create a Service definition for your todo-app Deployment in a YAML file.
  
- Apply the Service definition to your K8s (minikube) cluster using the `kubectl apply -f service.yml -n <namespace-name>` command.

  kubetl apply -f serviceexpose.yaml
  
- Verify that the Service is working by accessing the todo-app using the Service's IP and Port in your Namespace.

## Task-2:

- Create a ClusterIP Service for accessing the todo-app from within the cluster
- Create a ClusterIP Service definition for your todo-app Deployment in a YAML file.
- Apply the ClusterIP Service definition to your K8s (minikube) cluster using the `kubectl apply -f cluster-ip-service.yml -n <namespace-name>` command.
- Verify that the ClusterIP Service is working by accessing the todo-app from another Pod in the cluster in your Namespace.

![image](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/797f36c5-4a71-464a-be1a-5c7239d0d6bd)


## Task-3:

- Create a LoadBalancer Service for accessing the todo-app from outside the cluster
- Create a LoadBalancer Service definition for your todo-app Deployment in a YAML file.
- Apply the LoadBalancer Service definition to your K8s (minikube) cluster using the `kubectl apply -f load-balancer-service.yml -n <namespace-name>` command.
- Verify that the LoadBalancer Service is working by accessing the todo-app from outside the cluster in your Namespace.

Struggling with Services? Take a look at this video for a step-by-step [guide](https://youtu.be/OJths_RojFA).

Need help with Services in Kubernetes? Check out the Kubernetes [documentation](https://kubernetes.io/docs/concepts/services-networking/service/) for assistance.

Happy Learning :)

[← Previous Day](../day33/README.md) | [Next Day →](../day35/README.md)
