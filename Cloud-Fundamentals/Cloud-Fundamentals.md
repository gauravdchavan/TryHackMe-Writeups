
# ☁️ Cloud Computing Fundamentals

**Platform:** TryHackMe
**Room:** Cloud Computing Fundamentals
**Status:** ✅ Completed
**Difficulty:** Beginner
**Topics:** Cloud Computing, IaaS, PaaS, SaaS, EC2, Cloud Regions, Cost Optimization

---

## 📌 Overview

This room introduced the fundamentals of **cloud computing** and explained how organizations use cloud services to access computing resources without having to maintain physical infrastructure.

The room covered different cloud deployment models, cloud service models, EC2 instances, regions, scalability, and cloud cost optimization.

---

## 🎯 Learning Objectives

* Understand the fundamentals of cloud computing
* Learn the difference between Public, Private, and Hybrid Cloud
* Understand IaaS, PaaS, and SaaS
* Learn the basics of Amazon EC2
* Understand cloud regions and instance types
* Learn how cloud resources can be created and managed
* Understand basic cloud cost optimization

---

# 📚 Task 1 — Introduction

Cloud computing allows users and organizations to access computing resources through the internet.

Instead of purchasing and maintaining physical servers, organizations can use cloud providers to create resources such as:

* Virtual machines
* Storage
* Networking
* Applications
* Databases

### Key Idea

> Cloud computing provides flexible and scalable access to computing resources when they are needed.

---

# ☁️ Task 2 — Cloud Computing Overview

## Public Cloud

A **Public Cloud** provides cloud infrastructure over the internet to multiple customers.

Examples include cloud services provided by:

* AWS
* Microsoft Azure
* Google Cloud

### Characteristics

* Shared cloud infrastructure
* Accessible over the internet
* Resources can be provisioned when needed
* Usually follows a pay-as-you-use model

---

## Private Cloud

A **Private Cloud** is designed for and dedicated to a single organization.

Organizations can have greater control over:

* Infrastructure
* Security
* Configuration
* Data

For example, an organization such as a bank may use private cloud infrastructure for sensitive systems.

---

## Hybrid Cloud

A **Hybrid Cloud** combines **public and private cloud environments**.

The two environments can work together and share data or resources when required.

```text
       Private Cloud
             │
             │
             ↕
       Hybrid Cloud
             ↕
             │
        Public Cloud
```

---

# 🏗️ Cloud Service Models

## IaaS — Infrastructure as a Service

IaaS provides basic virtual infrastructure such as:

* Virtual machines
* CPU and memory resources
* Storage
* Networking

The cloud provider manages the underlying physical infrastructure, while the customer manages things such as the operating system, applications, and configuration.

### Example

**Amazon EC2**

> IaaS = "Give me the infrastructure; I'll manage my environment."

---

## 🛠️ PaaS — Platform as a Service

PaaS provides a **ready-to-use environment for developing and running applications**.

The cloud provider manages much of the underlying infrastructure and platform, allowing developers to focus mainly on their applications.

> PaaS = "Give me a platform; I'll build my application."

---

## 💻 SaaS — Software as a Service

SaaS provides a **complete software application** that users can access over the internet.

The user does not need to manage the underlying infrastructure or application.

### Examples

* Gmail
* Google Drive
* Zoom

> SaaS = "Give me the finished software; I'll use it."

---

## 🧠 Easy Comparison

| Model    | What you get         | Main responsibility             |
| -------- | -------------------- | ------------------------------- |
| **IaaS** | Infrastructure       | Manage OS, apps & configuration |
| **PaaS** | Development platform | Focus mainly on application     |
| **SaaS** | Finished software    | Simply use the software         |

### Easy way to remember

```text
IaaS → Infrastructure → Manage more
PaaS → Platform        → Build applications
SaaS → Software        → Use applications
```

---

# 🖥️ Task 3 — Deploying a Cloud Instance

The room provided a simulated cloud console where virtual machines could be created and managed.

## EC2

**EC2 (Elastic Compute Cloud)** represents a virtual computer/server in the cloud.

An EC2 instance can have:

* CPU
* Memory (RAM)
* Storage
* Operating System
* Network connectivity

EC2 instances can be created, configured, started, and stopped when required.

---

## 🌍 Cloud Region

A **Region** represents a geographical location where cloud resources are hosted.

Examples include regions in:

* North America
* Europe
* Asia

Choosing a region determines where your cloud resources are deployed.

---

## ⚙️ Instance Type

An **instance type** determines the resources and performance of a virtual machine.

For example:

* `t3.micro` → smaller instance
* `m5.large` → more powerful instance
* `t3a.small` → small instance

Generally:

> More resources → More computing power → Higher cost

---

# 🖥️ Lab Machines Created

During the practical exercise, the following machines were created:

| Instance Name           | Instance Type | Status  |
| ----------------------- | ------------- | ------- |
| `application-interface` | `t3.micro`    | Running |
| `study-machine-1`       | `m5.large`    | Stopped |
| `study-machine-2`       | `m5.large`    | Stopped |
| `study-machine-3`       | `t3a.small`   | Running |

---

# 💰 Billing & Cost Optimization

The room demonstrated that cloud resources have associated costs.

Different instance types can have different costs depending on their resources.

For example:

```text
t3.micro
   ↓
Smaller resources
   ↓
Lower cost

m5.large
   ↓
More resources
   ↓
Higher cost
```

When the application was still under development, the two study machines were **stopped** because they were not currently required.

### Key Concept

> **Unused cloud resources should be stopped or removed when they are not needed to reduce unnecessary costs.**

This is an important cloud **cost optimization** practice.

---

# 🎯 Key Cloud Computing Benefits

The room highlighted several important benefits of cloud computing:

### 1. Scalability

Resources can be increased or decreased according to demand.

### 2. On-Demand Self-Service

Users can create and manage resources whenever they need them.

### 3. Pay Only for What You Use

Cloud services commonly follow usage-based pricing models.

### 4. Security

Cloud providers offer various security mechanisms and services.

### 5. High Availability

Cloud infrastructure can be designed to remain available even when individual resources fail.

### 6. Global Access

Cloud services can be accessed from different locations through the internet.

---

# 🧠 Key Terminology

| Term              | Meaning                                                       |
| ----------------- | ------------------------------------------------------------- |
| **Public Cloud**  | Cloud infrastructure shared by multiple customers             |
| **Private Cloud** | Cloud infrastructure dedicated to one organization            |
| **Hybrid Cloud**  | Combination of public and private cloud                       |
| **IaaS**          | Infrastructure as a Service                                   |
| **PaaS**          | Platform as a Service                                         |
| **SaaS**          | Software as a Service                                         |
| **EC2**           | Virtual computers provided by AWS                             |
| **Region**        | Geographical location where cloud resources are hosted        |
| **Instance Type** | Defines the resources/performance of a virtual machine        |
| **Scalability**   | Ability to increase or decrease resources according to demand |

---

# 🔐 Cybersecurity Relevance

Cloud computing is highly relevant to cybersecurity because modern security environments often run in the cloud.

Understanding cloud infrastructure helps security professionals work with:

* Cloud servers
* Virtual machines
* Network security
* Access control
* Security monitoring
* SIEM platforms
* Cloud logging
* Incident response
* Vulnerability management

Cybersecurity professionals need to understand how cloud infrastructure works before they can properly secure it.

---

# 📝 Key Takeaways

* Cloud computing provides computing resources over the internet.
* **Public, Private, and Hybrid** are different cloud deployment models.
* **IaaS, PaaS, and SaaS** are the main cloud service models.
* **EC2** provides virtual computers in AWS.
* A **Region** represents a geographical location for cloud resources.
* **Instance types** determine the resources available to virtual machines.
* Cloud resources can be created and managed on demand.
* Stopping unused resources can reduce unnecessary costs.
* Cloud computing provides scalability, flexibility, high availability, and global access.

---

## 🏆 Room Completion

**Cloud Computing Fundamentals — Completed ✅**

![TryHackMe Cloud Computing Fundamentals Completion](cloud-computing-fundamentals.png)

### Next Recommended Topic

➡️ **Operating Systems Introduction**

Understanding operating systems is important for cybersecurity because cloud servers and applications ultimately run on operating systems.
