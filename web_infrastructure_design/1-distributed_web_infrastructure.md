# 📘 Explanation of Infrastructure Components

## 1. Why Add Two Web Servers?

Adding a second web server enhances **redundancy** and **scalability**. If one server crashes, the other continues to serve traffic, minimizing downtime. It also helps balance the workload, ensuring better performance under high demand.

## 2. Why Use a Load Balancer (HAProxy)?

A load balancer ensures that traffic is evenly spread across multiple web servers. This prevents overload on a single machine and increases overall **availability** and **fault tolerance** of the system.

## 3. What Load Balancing Algorithm Is Used?

The system uses the **round-robin** algorithm, which distributes incoming requests sequentially across the servers. Example:

- Request 1 → Server A  
- Request 2 → Server B  
- Request 3 → Server A  
- Request 4 → Server B  

This simple method guarantees **even traffic distribution**.

## 4. Active-Active vs. Active-Passive Setup

- **Active-Active**: All servers operate at the same time and share the load. This approach improves **efficiency** and **resource utilization**.  
- **Active-Passive**: Only one server is active while the other remains on standby. It improves **fault tolerance** but underuses available hardware.  

👉 In this setup, the load balancer follows an **Active-Active** configuration.

## 5. How Does a Primary-Replica (Master-Slave) Database Cluster Work?

- The **Primary node** manages all **write** operations (INSERT, UPDATE, DELETE) and sends data changes to the **Replica node**.  
- The **Replica node** is used for **read** operations (SELECT) and stays synchronized with the primary.  

This setup enhances **read performance** and ensures **data redundancy**.

## 6. Application View: Primary vs. Replica Nodes

- The **Primary** node is accessed for writing data, ensuring consistency and integrity.  
- The **Replica** node is used for read-only operations, reducing pressure on the primary and improving responsiveness.

---

# ❗ Infrastructure Weaknesses

## 1. Single Points of Failure (SPOF)

- **Load Balancer**: If the load balancer fails, no traffic can reach the web servers.  
- **Primary Database Node**: A failure here blocks all write operations until another node is promoted.

## 2. Security Flaws

- **No Firewall**: Leaves the system exposed to external threats like DDoS attacks or unauthorized access.  
- **No HTTPS**: Data is transmitted in plain text, making it vulnerable to interception.

## 3. Lack of Monitoring

Without a monitoring system, it becomes difficult to detect server crashes, traffic spikes, or performance issues in real time. This results in delayed responses to critical problems.

---

