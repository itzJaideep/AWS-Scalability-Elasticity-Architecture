# AWS-Scalability-Elasticity-Architecture
A hands-on implementation of AWS auto-scaling infrastructure that handles unpredictable traffic surges automatically using EC2, Application Load Balancer, Auto Scaling Group, and CloudWatch.

---

## Problem Statement

Traditional infrastructure struggles with unpredictable traffic surges — servers either crash under load or sit idle wasting money. This project demonstrates how AWS solves this using scalability and elasticity.

---

## Architecture

```
Internet Users
      |
      v
Application Load Balancer (Public Subnet)
      |
      v
+--------------------------------+
|     Auto Scaling Group         |
|  +------+  +------+  +------+  |
|  | EC2  |  | EC2  |  | EC2  |  |
|  +------+  +------+  +------+  |
|  (min:1  desired:2  max:5)     |
+--------------------------------+
      |
      v
  CloudWatch Alarms
  CPU > 50% → Scale Out
  CPU < 20% → Scale In
```

---

## AWS Services Used

| Service | Type | Configuration | Purpose |
|---|---|---|---|
| App Load Balancer | Load Balancer | HTTP/HTTPS, Round Robin | Distributes traffic across EC2 instances |
| EC2 Instances | Virtual Server | t2.micro, Amazon Linux 2023 | Hosts the web application |
| Auto Scaling Group | Scaling Service | Min:1 \| Desired:2 \| Max:5 | Auto adds/removes EC2 based on load |
| CloudWatch | Monitoring | CPU >50% scale out, <20% scale in | Triggers scaling policies automatically |
