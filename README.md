# 🚀 Datadog Monitoring Setup on AWS EC2

## 📌 Project Overview

This project demonstrates the setup of Datadog Agent on an AWS EC2 instance to monitor system-level metrics such as CPU, memory, disk usage, and network activity in real time.

---

## 🧱 Architecture Diagram

```mermaid
flowchart LR
    A[User / DevOps Engineer] --> B[AWS EC2 Instance (Ubuntu)]
    B --> C[Datadog Agent]
    C --> D[Datadog Cloud Platform]
    D --> E[Metrics Dashboard]
    D --> F[Alerts & Notifications]

    subgraph EC2 Instance
        B
        C
    end

    subgraph Datadog Platform
        D
        E
        F
    end
```

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

## 👨‍💻 Author

Kishan
DevOps Enthusiast | AWS | Monitoring & Observability
