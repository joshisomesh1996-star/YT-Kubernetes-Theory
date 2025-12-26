# Distributed Computing

Distributed computing refers to a system where multiple computers (or nodes) work together to solve a large problem or process data collaboratively. The tasks are divided among the nodes, enabling parallel processing for faster and more efficient computation.

---

## Components of Distributed Computing

### Cluster
A cluster is a group of interconnected computers or servers that work together as a single system. Each computer in the cluster is called a node, and they collaborate to share workloads, provide redundancy, and improve performance.

### Lead-Node Server
The lead-node (or master node) in a distributed system is responsible for managing the cluster. It coordinates tasks like assigning workloads to worker nodes, monitoring their health, and ensuring everything runs smoothly.

### Communication
Communication in distributed computing refers to how nodes in the cluster exchange data and instructions. It happens through network protocols and is crucial for synchronization, task distribution, and data sharing among nodes.

### Concurrency (Speed, Fault Tolerance)
Concurrency in distributed systems allows multiple tasks to run simultaneously across nodes. This boosts speed and ensures fault tolerance—if one node fails, the workload is shifted to others, preventing disruptions.

### Comparison with Apache Spark Internally (MapReduce)
Apache Spark and Kubernetes both enable distributed computing but operate differently. Spark uses a specialized model called **MapReduce**, where tasks are divided into "map" (processing) and "reduce" (aggregation) steps. Kubernetes, on the other hand, provides a general-purpose framework for orchestrating containerized workloads and does not impose a specific computation model.

---

## Benefits of Distributed Computing

### Scalability
Distributed computing allows you to divide tasks among multiple machines, enabling the system to handle larger workloads. For example, in ML, if training a model on a single machine takes 10 hours, distributing the work across 10 machines can reduce the time significantly.

### Fault Tolerance
If one machine fails, the distributed system can redistribute the tasks to other machines, ensuring the system keeps running. Think of it as a power grid—if one station goes offline, others take over to maintain the electricity supply.

### Improved Performance
Tasks are processed in parallel, reducing overall latency and making applications faster. For example, web applications can serve more users simultaneously by running requests on multiple servers.

### Cost Efficiency
Instead of investing in expensive, high-performance hardware, you can use multiple cheaper machines to achieve the same (or better) results.

### Flexibility
You can use a mix of different types of machines, hardware, or even cloud providers. This makes it easier to build and manage systems that adapt to changing needs.

---

## Microservices: The Real-World Scenario

Imagine you are building a machine learning system to recommend movies to users (like Netflix). This ML system has several components:

1. **Data Ingestion**  
   Collects and processes data from users (e.g., their watch history and ratings).

2. **Feature Engineering**  
   Transforms raw data into meaningful inputs for your ML model.

3. **Model Training**  
   Continuously trains and updates your recommendation algorithm.

4. **Model Serving**  
   Hosts the trained model and responds to user requests in real time.

5. **User Interface**  
   Provides the website or app where users can browse and see recommendations.

---

### Monolithic Architecture

In the traditional **monolithic architecture**, all these components would be bundled into a single application. If you wanted to scale the system (e.g., if user requests increased), you would have to scale the entire application, even if only the **Model Serving** component needed more resources.

---

## Microservices in Action

Instead of bundling everything together, microservices break down the application into smaller, independent components. Each component is responsible for a single task and can run, scale, and be updated independently.

For our ML system:

1. **Data Ingestion Service**  
   Runs independently, continuously collecting and processing data.

2. **Feature Engineering Service**  
   Operates on processed data and outputs features for the model.

3. **Training Service**  
   Triggers model retraining when new data arrives or at scheduled intervals.

4. **Model Serving Service**  
   Hosts the model, answering API requests like:  
   *“What movies should User123 watch?”*

5. **UI Service**  
   Displays the user interface and connects to the backend services.

This separation makes it easy to scale just the **Model Serving Service** when the number of user requests spikes, without affecting the other parts of the system.

---

## Real-Life Analogy for Microservices: Food Court

- Each food stall specializes in one type of cuisine (e.g., burgers, pizza, coffee).
- They operate independently, so if one stall runs out of ingredients (or needs upgrades), it doesn’t affect the others.
- Customers (users) can pick and choose what they want, and the food court manager (**Kubernetes**) ensures all stalls have the resources they need to function.

---

## Challenges of Distributed Computing

- **Resource Management**  
  Allocating resources like CPU, memory, and storage across machines is complex.

- **Scaling**  
  Adding or removing machines from the system requires significant effort.

- **Communication and Networking**  
  Network failures, latency, and configuration errors can cause major issues.

- **Fault Handling**  
  Detecting failures, recovering data, and rerouting tasks with minimal downtime.

- **Load Balancing**  
  Even distribution of workloads across machines is non-trivial.

- **Configuration and Deployment**  
  Managing deployments across many machines is error-prone.

- **Monitoring and Debugging**  
  Logs and metrics are spread across multiple systems.

---

# How Kubernetes Addresses These Challenges

Kubernetes is a **container orchestration platform** designed to handle distributed systems.

## Key Features

1. **Automated Resource Management**  
   Schedules workloads based on resource availability.

2. **Effortless Scaling**  
   Add or remove pods by changing configuration values.

3. **Reliable Networking**  
   Built-in pod-to-pod communication.

4. **Self-Healing**  
   Automatically restarts or reschedules failed pods.

5. **Load Balancing**  
   Distributes traffic evenly across pods.

6. **Simplified Deployment**  
   Uses declarative YAML configuration files.

7. **Centralized Monitoring and Debugging**  
   Integrates with tools like Prometheus and ELK Stack.

---

# Kubernetes Internals

### Master Node (Control Plane)
The brain of the cluster that manages workloads and monitors system health.

### Resource Manager
Ensures efficient allocation of CPU, memory, and storage.

### API Server
The interface through which users interact with Kubernetes.

### Database (etcd)
Stores cluster state and configuration data.

### Worker Node
Executes application workloads.

### Kubelet
Ensures containers are running as expected on worker nodes.

### Kube-Proxy
Manages network traffic and routing.

### Pods
The smallest deployable unit in Kubernetes.

### SharedDB (Volumes)
Shared storage used by pods.

### Kube-Manifests (YAML)
Blueprints defining how applications should run.

### Service
Provides a stable endpoint for accessing pods.

### Namespace
Logical isolation within a cluster.

### Scheduler
Assigns pods to nodes based on resource availability.

### ReplicaSets
Ensures a fixed number of pod replicas are always running.

---

## Real-Life Analogy: Distributed Computing With and Without Kubernetes

### Without Kubernetes
Manually managing failures, scaling, and deployments—chaotic and error-prone.

### With Kubernetes
Automatic monitoring, scaling, healing, and load distribution.

---

## Connecting Microservices to Docker and Kubernetes

### Docker: Packaging the Microservices

Each microservice runs inside its own Docker container.

- Containers include all dependencies
- Lightweight and portable
- Run consistently across environments

### Kubernetes: Orchestrating the Microservices

1. **Scaling**  
   Automatically increases replicas when load spikes.

2. **Networking**  
   Handles inter-service communication.

3. **Load Balancing**  
   Distributes traffic across replicas.

---

## Advantages of Microservices for ML in Docker-Kubernetes

1. **Independent Scaling**
2. **Resilience**
3. **Flexibility in tools and languages**

---

## Summary

- Distributed computing provides scalability, fault tolerance, and performance.
- Microservices break complex ML systems into manageable services.
- Docker packages services consistently.
- Kubernetes orchestrates and manages distributed workloads efficiently.
