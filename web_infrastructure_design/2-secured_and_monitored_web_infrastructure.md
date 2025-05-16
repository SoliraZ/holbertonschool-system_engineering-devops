# 🔐 Explanation of Additional Security and Monitoring Elements

## 1. Why Deploy Three Firewalls?

Adding multiple firewalls helps reinforce network security by:

- Blocking unauthorized access to internal systems.  
- Filtering both inbound and outbound traffic based on predefined security rules.  
- Protecting the infrastructure from common attacks such as **DDoS**, **brute-force attempts**, and **unauthorized intrusion**.

## 2. Why Use HTTPS for Web Traffic?

Serving content over HTTPS ensures that all communication between the client and server is **encrypted**. Benefits include:

- **Confidentiality**: Prevents eavesdropping by encrypting data.  
- **Integrity**: Ensures that data is not altered during transit.  
- **Authentication**: Confirms the legitimacy of the server to users.

## 3. Why Install Monitoring Clients?

Monitoring agents are crucial for system health and performance. They allow administrators to:

- Track key metrics (CPU usage, memory, disk space).  
- Identify anomalies such as high traffic, crashes, or slowdowns.  
- Make informed decisions about scaling and optimization.

## 4. How Does the Monitoring Tool Collect Data?

Agents (e.g., **Sumologic**, **Prometheus node exporters**) are installed on each server. They:

- Continuously gather system and application metrics.  
- Transmit the data to a centralized platform.  
- Visualize the data via dashboards for real-time analysis and alerting.

## 5. How to Monitor Web Server QPS (Queries Per Second)?

To monitor QPS:

- Use monitoring dashboards to measure how many HTTP requests are handled per second.  
- Set thresholds and configure alerts for sudden drops or spikes.  
- Analyze trends to identify bottlenecks and scale services efficiently.

---

# ⚠️ Infrastructure Weaknesses & Potential Issues

## 1. SSL Termination at the Load Balancer

- **Problem**: If SSL encryption ends at the load balancer, internal communication between the load balancer and web servers happens in plain text, creating a security risk.
- **Recommendation**: Implement **end-to-end encryption** by enabling HTTPS on the backend web servers too.

## 2. Single Writable MySQL Server

- **Problem**: The primary database is a **single point of failure** for write operations. If it becomes unavailable, data writes cannot proceed.
- **Recommendation**: Use a **multi-primary** setup or adopt a **distributed database** solution to enhance availability.

## 3. Servers Hosting All Components Together

- **Problem**: When each server runs all services (web, app, database), a failure in one service may affect the entire stack on that server.
- **Recommendation**: Follow the **separation of concerns** principle by distributing services across different machines. This enhances **fault isolation** and **scalability**.

---

