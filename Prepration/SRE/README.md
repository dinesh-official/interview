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




