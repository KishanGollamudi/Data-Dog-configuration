# 🚀 Datadog Monitoring Setup on AWS EC2

## 📌 Project Overview

This project demonstrates the setup of **Datadog Agent** on an AWS EC2 instance to monitor system-level metrics such as CPU, memory, disk usage, and network activity in real time.

The implementation showcases practical DevOps skills including agent installation, troubleshooting, configuration, and monitoring validation.

---

## 🧱 Architecture

EC2 Instance (Ubuntu)
↓
Datadog Agent
↓
Datadog Cloud Dashboard
↓
Metrics Visualization & Alerts

---

## 🛠️ Tools & Technologies

* AWS EC2 (Ubuntu 24.04)
* Datadog Agent v7
* Linux CLI
* Cloud Monitoring & Observability

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

✅ Expected:

* Agent running
* CPU, Memory, Disk checks active

---

### 5️⃣ Configure Agent (if needed)

```bash
sudo nano /etc/datadog-agent/datadog.yaml
```

```yaml
api_key: <YOUR_API_KEY>
site: datadoghq.com
```

Restart agent:

```bash
sudo systemctl restart datadog-agent
```

---

## 🔍 Troubleshooting

### ❌ Issue: API Key Invalid (403 Errors)

**Cause:**

* Used Application Key instead of API Key
* Wrong region (EU vs US)
* Incorrect key copy

**Fix:**

* Generate new API key from Datadog
* Ensure correct site (`datadoghq.com`)
* Restart agent

---

### ❌ Issue: Host Not Visible

**Fix:**

* Check agent status
* Verify API key
* Restart service

---

## 📊 Validation

After successful setup:

👉 Navigate to:

* Datadog → Infrastructure → Hosts

You should see:

* EC2 instance listed
* CPU usage graph
* Memory usage
* Disk metrics

---

## 🧪 Load Testing

Simulate CPU load:

```bash
yes > /dev/null &
```

Stop process:

```bash
killall yes
```

---

## 🔔 (Optional) Alert Setup

* Navigate to: Monitoring → Monitors
* Create CPU alert:

  * Metric: `system.cpu.user`
  * Threshold: > 80%

---

## 🚀 Key Learnings

* Agent-based monitoring setup
* Debugging authentication errors (API key issues)
* Region mismatch troubleshooting
* Real-time infrastructure observability

---

## 📈 Outcome

* Successfully integrated EC2 with Datadog
* Enabled real-time monitoring
* Verified metric collection and visualization
* Built production-level monitoring setup

---

## 🔮 Future Enhancements

* Log monitoring integration
* Docker container monitoring
* Kubernetes (EKS) monitoring
* Terraform automation for deployment

---

## 👨‍💻 Author

Kishan
DevOps Enthusiast | AWS | Monitoring & Observability

---

