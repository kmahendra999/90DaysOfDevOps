## Day 37 Task: Kubernetes Important interview Questions.

## Questions

Hit the link if you are preparing for interview

https://github.com/kmahendra999/DevOpsInterviewQuestions/blob/main/Most%2095%25%20Interview%20question%20for%20devops.docx

1.What is Kubernetes and why it is important?

2.What is difference between docker swarm and kubernetes?

3.How does Kubernetes handle network communication between containers?

4.How does Kubernetes handle scaling of applications?

5.What is a Kubernetes Deployment and how does it differ from a ReplicaSet?

6.Can you explain the concept of rolling updates in Kubernetes?

7.How does Kubernetes handle network security and access control?

8.Can you give an example of how Kubernetes can be used to deploy a highly available application?

9.What is namespace is kubernetes? Which namespace any pod takes if we don't specify any namespace?

10.How ingress helps in kubernetes?

11.Explain different types of services in kubernetes?

12.Can you explain the concept of self-healing in Kubernetes and give examples of how it works?

13.How does Kubernetes handle storage management for containers?

14.How does the NodePort service work?

15.What is a multinode cluster and single-node cluster in Kubernetes?

16.Difference between create and apply in kubernetes?


<code>
1. Kubernetes: An open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. Important for efficient container orchestration and management.

2. Docker Swarm vs. Kubernetes:
Swarm: Built by Docker, simpler setup, suitable for smaller deployments.
Kubernetes: More robust, handles larger-scale container orchestration with advanced features.
Kubernetes Network Communication:

3. Uses a container network interface (CNI) to enable communication between containers.
Pods share an IP address and port space within a cluster.
Scaling in Kubernetes:

4. Horizontal Pod Autoscaling automatically adjusts the number of pods.
Vertical Pod Autoscaling adjusts the resources allocated to individual pods.
Kubernetes Deployment vs. ReplicaSet:

5. Deployment: Manages application lifecycle, supports rolling updates, and rollbacks.
ReplicaSet: Ensures a specified number of replicas are running.

6. Rolling Updates in Kubernetes:
Gradual replacement of old pods with new ones, ensuring continuous service availability during updates.
Kubernetes Network Security:

7. Network Policies control traffic between pods.
Role-Based Access Control (RBAC) manages user access to cluster resources.
Highly Available Application in Kubernetes:

8. Use multiple replicas of applications.
Deploy across multiple nodes and zones.

9. Kubernetes Namespace:
Logical partition within a cluster.
Pods without a specified namespace go to the "default" namespace.

10. Ingress in Kubernetes:
Manages external access to services.
Routes traffic based on rules defined by the user.

11. Types of Services in Kubernetes:
ClusterIP: Exposes service within the cluster.
NodePort: Exposes service on each node's IP and a static port.
LoadBalancer: Exposes service externally using a cloud provider's load balancer.

12. Self-Healing in Kubernetes:
Monitors the state of applications.
Automatically replaces failed or unhealthy containers.

13. Storage Management in Kubernetes:
Uses Persistent Volumes (PV) and Persistent Volume Claims (PVC) for storage.

14. NodePort Service in Kubernetes:
Exposes a service on a static port on each node.
Allows external access to the service.

15. Multinode Cluster vs. Single-Node Cluster:
Multinode: Multiple interconnected nodes distribute workload.
Single-Node: All components run on a single machine, suitable for development or testing.

16. Create vs. Apply in Kubernetes:
Create: Creates a resource, fails if already exists.
Apply: Creates or updates a resource, updates if already exists.
</code>


## These questions will help you in your next DevOps Interview.

_Write a Blog and share it on LinkedIn._

**_Happy Learning :)_**

[← Previous Day](../day36/README.md) | [Next Day →](../day38/README.md)
