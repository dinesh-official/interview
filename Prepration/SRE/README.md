### **1️⃣ What is the role of an SRE in a product engineering company?**

> **“An SRE ensures the product runs reliably, is scalable, and available for users. They automate repetitive tasks, monitor systems, handle production issues, and work with developers so features can be released safely.”**

**Memory trick:** Reliability + Automation + Collaboration

---

### **2️⃣ How is SRE different from DevOps in real projects?**

> **“DevOps is a culture focused on collaboration, automation, and faster delivery. SRE applies engineering to operations with a focus on reliability, using SLOs and error budgets. In real projects, DevOps builds pipelines and processes; SRE ensures the system stays stable while releasing features.”**

**Memory trick:** DevOps = culture, SRE = engineering reliability

---

### **3️⃣ How do you implement SLOs for customer-facing applications?**

> **“I identify user-focused SLIs like availability, latency, error rate, and throughput. Then I define SLO targets, monitor them with Prometheus/Grafana, use error budgets to balance releases and reliability, and review incidents to improve.”**

**Memory trick:** SLIs → SLOs → Monitor → Error Budgets → Improve

---

### **4️⃣ What is an error budget and how do you use it practically?**

> **“An error budget is the amount of acceptable failure while meeting SLOs. For example, if availability is 99.9%, the system can fail 0.1% of the time. I use it to decide whether to release features or pause releases, and to prioritize fixing issues before they impact users.”**

**Memory trick:** Allowed failures → guide releases → fix problems

---

### **5️⃣ How do you measure reliability in production?**

> **“I measure reliability using SLIs like availability, latency, error rate, and throughput. I track these against SLOs, monitor them with tools, use error budgets to manage risk, and review incidents to continuously improve.”**

**Memory trick:** SLIs → SLOs → Monitor → Error Budgets → Improve

---

### **6️⃣ How do you reduce operational toil?**

> **“I reduce toil by automating repetitive tasks like deployments and monitoring, creating small scripts or CI/CD improvements, and setting up alerts so I don’t have to manually check systems.”**

**Memory trick:** Automate repetitive work → use CI/CD → set up alerts

---

### **7️⃣ When do you say NO to a release?**

> **“I say no when the system is unstable, SLOs are not met, or the error budget is exhausted. Releasing under these conditions could affect users, so I pause until issues are fixed.”**

**Memory trick:** Unstable system → SLOs failing → error budget exhausted

---

### **8️⃣ How do you bring reliability culture to dev teams?**

> **“I make reliability visible by sharing SLOs and error budgets in meetings. I suggest small improvements like monitoring, alerts, or tests, and encourage teams to fix issues proactively before they affect users.”**

**Memory trick:** Make visible → suggest improvements → fix early

---
2️⃣ Kubernetes (VERY COMMON – HANDS-ON FOCUS)
---
### **Explain Kubernetes architecture.**
### **Kubernetes Architecture – Simple Explanation**

**Kubernetes** is a system to manage containerized applications across clusters of machines. Its architecture has **two main components**:



### **1️⃣ Control Plane (Master)**

* Manages the cluster and makes decisions.
* **Components:**

  1. **API Server** – The entry point for all commands (`kubectl`) and internal communication.
  2. **etcd** – Key-value store that stores all cluster data (configuration, state).
  3. **Controller Manager** – Monitors cluster state and makes changes to reach the desired state.
  4. **Scheduler** – Assigns pods to nodes based on resources, policies, and availability.

---

### **2️⃣ Worker Nodes**

* Where applications actually run.
* **Components:**

  1. **Kubelet** – Agent on each node, communicates with API server, ensures containers are running.
  2. **Kube-Proxy** – Handles network routing for services inside the cluster.
  3. **Container Runtime** – Runs containers (Docker, containerd, etc.).

---



---
Why do pods go into CrashLoopBackOff?
---

### **CrashLoopBackOff – Simple Explanation**

> **“A pod goes into CrashLoopBackOff when its container keeps crashing after starting. Kubernetes tries to restart it, but if it keeps failing repeatedly, it stops and shows CrashLoopBackOff.”**

---

### **Common reasons for this**

1. **Application errors** – The app inside the container crashes immediately (e.g., missing file, wrong config, or code bug).
2. **Incorrect command or entrypoint** – The container’s startup command fails.
3. **Resource limits** – Container exceeds CPU or memory limits and gets killed.
4. **Dependency issues** – Required service, database, or config isn’t available.
5. **Crash on health check** – Readiness or liveness probes fail repeatedly.

---
Difference between readiness and liveness probes?
--- 
“A liveness probe checks if a container is alive. If it fails, Kubernetes restarts the container. A readiness probe checks if a container is ready to serve traffic. If it fails, Kubernetes stops sending requests to it, but doesn’t restart it.”

Memory Trick (easy to recall)

Liveness → “Is it alive?” → restart if dead

Readiness → “Is it ready?” → remove from service if not ready

Quick Example

Liveness probe: Your app crashes or hangs → container restarts.

Readiness probe: App is still starting up → traffic is not sent until ready.

---
How do you troubleshoot a failing pod?
---

When a pod is failing, I first check its status with kubectl get pods and then look at the events using kubectl describe pod <pod-name> to see why it’s failing. Next, I check the container logs with kubectl logs <pod-name> to find errors. I also verify configs, environment variables, secrets, and resource limits. Finally, I fix the root cause and restart or redeploy the pod.


Step-by-step memory trick

Check pod status → kubectl get pods

Check events → kubectl describe pod <pod>

Check logs → kubectl logs <pod>

Check configs & env → secrets, ConfigMaps, resources

Fix & restart → redeploy or scale

---
What happens if a node goes down?
---

If a node goes down, Kubernetes detects it using the node controller. All pods on that node are marked as ‘NotReady.’ Depending on their configuration, the scheduler automatically tries to reschedule the pods on other healthy nodes to keep the application running.

---
How does HPA work?
---
HPA automatically scales the number of pods in a deployment or replica set based on resource usage, like CPU, memory, or custom metrics. It continuously monitors the metrics and increases or decreases pods to maintain the target performance.

