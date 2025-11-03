Absolutely bro 🔥 — here’s a clean, professional **README.md** you can drop directly into your `task8` folder in VS Code.
It summarizes **everything you’ve done**, including setup, commands, and outcomes 👇

---

## 🛰️ IoT-Sensor-API — Kubernetes Autoscaling Demo

### 📘 **Overview**

This project demonstrates **Horizontal Pod Autoscaling (HPA)** in Kubernetes using a sample application called **IoT Sensor API**.
The goal is to automatically scale the number of running pods based on **CPU utilization**.

---

### ⚙️ **Project Structure**

```
k8s-autoscale-demo/
│
└── task8/
    ├── iot-sensor-deployment.yaml      # Deployment & Service for IoT API
    ├── iot-sensor-hpa.yaml             # Horizontal Pod Autoscaler
    ├── load-generator.yaml             # Load generator to simulate CPU load
    └── README.md                       # Project documentation
```

---

### 🚀 **Steps Performed**

1️⃣ **Create and Deploy the Application**

```bash
kubectl apply -f iot-sensor-deployment.yaml
```

* Deploys the IoT Sensor API app with defined CPU/memory limits.

2️⃣ **Configure Horizontal Pod Autoscaler**

```bash
kubectl apply -f iot-sensor-hpa.yaml
```

* Sets `minPods=1`, `maxPods=5`, `targetCPU=50%`.

3️⃣ **Deploy the Load Generator**

```bash
kubectl apply -f load-generator.yaml
```

* Simulates high CPU load to trigger autoscaling.

4️⃣ **Monitor the Autoscaler**

```bash
kubectl get hpa -w
```

* Watches CPU usage and replica count increase automatically.

---

### 📈 **Expected Output**

* Initially, 1 pod is running.
* When CPU usage exceeds 50%, HPA automatically increases replicas (e.g., 1 → 3 → 5).
* When load decreases, replicas reduce back to 1.

**Example Output:**

```
NAME                 REFERENCE                     TARGETS             MINPODS   MAXPODS   REPLICAS   AGE
iot-sensor-api-hpa   Deployment/iot-sensor-api     cpu: 75%/50%        1         5         3          10m
```

---

### 🎯 **Result**

✅ Kubernetes automatically scaled the **IoT Sensor API** application based on real-time CPU metrics.
✅ Demonstrates efficient resource utilization and auto-healing features of Kubernetes.

---

### 🧠 **Key Learnings**

* Difference between **Docker** (containerization) and **Kubernetes** (orchestration).
* Role of **Metrics Server** in HPA.
* How to observe autoscaling using real-time resource monitoring.

---

### 👨‍💻 **Commands Summary**

```bash
kubectl get pods
kubectl get hpa
kubectl logs <loadgen-pod-name>
kubectl delete pod <pod-name>
kubectl top pods
```

