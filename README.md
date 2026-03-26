# 🚀 Datadog Monitoring Setup on AWS EC2

## 📌 Project Overview

This project demonstrates the setup of Datadog Agent on an AWS EC2 instance to monitor system-level metrics such as CPU, memory, disk usage, and network activity in real time.

<img width="1128" height="383" alt="image" src="https://github.com/user-attachments/assets/2f5aa58b-30f6-462d-aeb2-e2e437132c2f" />

---

## 🧱 Architecture Diagram
<img width="887" height="910" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/cb5be949-219a-4396-970d-df382d783aa8" />

---

## 🛠️ Tools & Technologies

* AWS EC2 (Ubuntu 24.04)
* Datadog Agent v7
* Linux CLI
* Datadog (Monitoring & Observability)

---

## 🎯 Objectives

* Install Datadog Agent on EC2
* Configure API authentication
* Enable infrastructure monitoring
* Visualize metrics in Datadog dashboard
* Validate real-time data flow

---

## ⚙️ Step-by-Step Setup

### 1️⃣ Launch EC2 Instance

* AMI: Ubuntu 24.04
* Instance Type: t2.micro
* Security Group: Allow SSH (port 22)

---

### 2️⃣ Connect to EC2

```bash
ssh ubuntu@<your-ec2-ip>
```

---

### 3️⃣ Install Datadog Agent

```bash
DD_API_KEY=<YOUR_API_KEY> DD_SITE="datadoghq.com" bash -c "$(curl -L https://install.datadoghq.com/scripts/install_script_agent7.sh)"
```

---

### 4️⃣ Verify Agent Status

```bash
sudo datadog-agent status
```

---

### 5️⃣ Configure Agent (if needed)

```bash
sudo nano /etc/datadog-agent/datadog.yaml
```

```yaml
api_key: <YOUR_API_KEY>
site: datadoghq.com
```

Restart:

```bash
sudo systemctl restart datadog-agent
```

---

## 🔍 Troubleshooting

### ❌ API Key Invalid (403)

* Ensure API key (not Application key)
* Verify correct region (datadoghq.com)
* Restart agent

---

## 📊 Validation

Go to:
👉 Infrastructure → Hosts

You should see:

* EC2 instance
* CPU, Memory, Disk metrics

---

## 🧪 Load Testing

```bash
yes > /dev/null &
killall yes
```

---

## 🔔 Alert Setup (Optional)

* Metric: `system.cpu.user`
* Threshold: > 80%

---

## 🚀 Key Learnings

* Agent-based monitoring
* Debugging API authentication issues
* Region mismatch troubleshooting
* Real-time observability setup

---

## 📈 Outcome

* Successfully integrated EC2 with Datadog
* Real-time monitoring enabled
* Metrics validated on dashboard

---

## 🔮 Future Enhancements

* Log monitoring
* Docker monitoring
* Kubernetes (EKS) integration
* Terraform automation

---
## 📘 Datadog Account, Trial & Key Concepts

### 🆓 Free Trial & Learner Account

Datadog provides a **14-day free trial** that allows users to explore its full monitoring and observability features without any cost.

When signing up on **datadoghq.com**, a **learner (individual) account** can be created using a personal email (e.g., Gmail). Although Datadog is designed for enterprise use, it fully supports individual users for learning and experimentation.

During the trial period:

* Full access to infrastructure monitoring features is available
* No credit card is required initially
* Suitable for DevOps labs, personal projects, and practice environments

---

### 🔑 API Key vs Application Key (Important Change)

Datadog uses two different types of keys, which often causes confusion:

#### ✅ API Key (Used in this project)

* Used by the **Datadog Agent**
* Responsible for sending metrics from EC2 to Datadog
* Must be configured in:
  `/etc/datadog-agent/datadog.yaml`

#### ❌ Application Key

* Used for Datadog API integrations and programmatic access
* NOT used for agent installation
* Using this key results in **403 errors (Invalid API Key)**

📌 **Recent UI Change:**

* API Keys are now located under:
  **Organization Settings → API Keys**
* Application Keys are under:
  **Personal Settings → Application Keys**

---

### 🧭 Region Awareness (Critical)

Datadog accounts are region-specific:

* `datadoghq.com` → US region
* `datadoghq.eu` → EU region

The following must always match:

* Login URL
* API Key source
* Agent configuration (`site:` field)

Mismatch leads to:

* Authentication failures
* HTTP 403 errors
* No data in dashboard

---

### ⚙️ Datadog Agent Placement (How It Works)

The **Datadog Agent** is installed **directly on the EC2 instance**.

#### 📍 Location on System:

* Configuration file:
  `/etc/datadog-agent/datadog.yaml`
* Service:
  `datadog-agent` (runs as a background service)

#### 🔄 Data Flow:

EC2 Instance
→ Datadog Agent (collects metrics)
→ Datadog Cloud Platform
→ Dashboard & Alerts

The agent continuously collects:

* CPU usage
* Memory usage
* Disk usage
* Network statistics

And securely sends them to Datadog servers using the API key.

---

### 🧠 Key Takeaways

* Datadog offers a **free 14-day trial** suitable for learning
* Always use **API Key (not Application Key)** for agent setup
* Ensure **region consistency** across setup
* Agent runs locally on EC2 and sends metrics to the cloud

---

## 👨‍💻 Author

Kishan
DevOps Enthusiast | AWS | Monitoring & Observability
