# Day 35: Mastering ConfigMaps and Secrets in Kubernetes🔒🔑🛡️

### 👏🎉 Yay! Yesterday we conquered Namespaces and Services 💪💻🔗🚀

## What are ConfigMaps and Secrets in k8s

In Kubernetes, ConfigMaps and Secrets are used to store configuration data and secrets, respectively. ConfigMaps store configuration data as key-value pairs, while Secrets store sensitive data in an encrypted form.

- _Example :- Imagine you're in charge of a big spaceship (Kubernetes cluster) with lots of different parts (containers) that need information to function properly.
  ConfigMaps are like a file cabinet where you store all the information each part needs in simple, labeled folders (key-value pairs).
  Secrets, on the other hand, are like a safe where you keep the important, sensitive information that shouldn't be accessible to just anyone (encrypted data).
  So, using ConfigMaps and Secrets, you can ensure each part of your spaceship (Kubernetes cluster) has the information it needs to work properly and keep sensitive information secure! 🚀_
- Read more about [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/) & [Secret](https://kubernetes.io/docs/concepts/configuration/secret/).

## Today's task:

## Task 1:

- Create a ConfigMap for your Deployment
- Create a ConfigMap for your Deployment using a file or the command line
- Update the deployment.yml file to include the ConfigMap
- Apply the updated deployment using the command: `kubectl apply -f deployment.yml -n <namespace-name>`
- Verify that the ConfigMap has been created by checking the status of the ConfigMaps in your Namespace.

<code>
root@instance:~/0903# ls
configmap.yml  deployment.yml
root@instance:~/0903# cat configmap.yml 
apiVersion: v1
kind: ConfigMap
metadata:
  name: todo-configmap
  namespace: dev
data:
  APP_NAME: "Todo App"
  ENVIRONMENT: "Development"
root@instance:~/0903# cat deployment.yml 
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app
  namespace: dev
  labels:
    app: todo
spec:
  replicas: 2
  selector:
    matchLabels:
      app: todo
  template:
    metadata:
      labels:
        app: todo
    spec:
      containers:
      - name: todo
        image: piyushsachdeva/todo-app:build-8
        ports:
        - containerPort: 3000
        envFrom:
        - configMapRef:
            name: todo-configmap

  
kubectl get ns
kubectl create ns dev
kubectl apply -f configmap.yml -n dev 
kubectl apply -f deployment.yml -n dev

kubectl exec -it todo-app-68f4b56ffb-6kbd4 -n dev -- sh

env command in the pod.
</code>

## Task 2:

- Create a Secret for your Deployment
- Create a Secret for your Deployment using a file or the command line
- Update the deployment.yml file to include the Secret
- Apply the updated deployment using the command: `kubectl apply -f deployment.yml -n <namespace-name>`
<code>
root@instance:~/0903# cat secret.yml 
apiVersion: v1
kind: Secret
metadata:
  name: todo-secret
  namespace: dev
type: Opaque
data:
  password: cmVkaGFy
root@instance:~/0903# cat deployment.yml 
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app
  namespace: dev
  labels:
    app: todo
spec:
  replicas: 2
  selector:
    matchLabels:
      app: todo
  template:
    metadata:
      labels:
        app: todo
    spec:
      containers:
        - name: todo
          image: piyushsachdeva/todo-app:build-8
          ports:
            - containerPort: 3000
          env:
            - name: PASSWORD
              valueFrom:
                secretKeyRef:
                  name: todo-secret
                  key: password


kubectl create ns dev
kubectl apply -f secret.yml -n dev
kubectl get secret -n dev
kubectl apply -f deployment.yml -n dev
kubectl get deploy -n dev
kubectl exec -it todo-app-d6848bf48-f7zhb -n dev -- sh
inside the pod
hit command echo $PASSWORD



</code>
- Verify that the Secret has been created by checking the status of the Secrets in your Namespace.

Need help with ConfigMaps and Secrets? Check out this [video](https://youtu.be/FAnQTgr04mU) for assistance.

Keep learning and expanding your knowledge of Kubernetes💥🙌

[← Previous Day](../day34/README.md) | [Next Day →](../day36/README.md)
