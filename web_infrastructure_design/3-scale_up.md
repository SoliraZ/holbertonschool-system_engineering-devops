# 🖥️ Web Infrastructure: Component Overview & Architecture Design

## 🔄 Roles of Web and Application Servers

In a well-structured web infrastructure, responsibilities are clearly divided:

- **Web Server**  
  Handles client HTTP/HTTPS requests, serves static content (e.g., HTML, CSS, JS), and forwards dynamic requests to the application layer.  
  **Examples**: `Nginx`, `Apache`.

- **Application Server**  
  Executes backend logic, processes dynamic content (like user authentication or data processing), and communicates with the database.  
  **Examples**: `Node.js`, `Django`, `Tomcat`.

---

## 📦 Infrastructure Requirements

To build a robust, scalable, and fault-tolerant infrastructure, the following components are essential:

### 1. 🧭 1 Web Server

- Accepts incoming HTTP/HTTPS traffic.  
- Serves static files directly.  
- Forwards dynamic requests to the application server.

### 2. ⚖️ 1 Load Balancer (HAProxy)

- Routes traffic evenly across backend servers.  
- Enhances availability and scalability.  
- **Cluster Setup**: Configured with a secondary HAProxy node for redundancy — if one node fails, the other maintains traffic flow.

### 3. 🔁 Component Separation

To optimize performance and reliability, infrastructure components are deployed on separate servers:

- **Web Server**  
  Manages HTTP/S traffic and static resources.

- **Application Server**  
  Handles dynamic content generation and business logic.

- **Database Server**  
  Responsible for secure and reliable data storage and retrieval.

---

## 🔍 Detailed Explanation of Key Elements

### 1. Why Use a Load Balancer (HAProxy)?

- **Purpose**: Prevents overload by distributing incoming traffic across multiple backend servers.  
- **Benefits**:
  - Ensures **high availability** — traffic continues even if a server fails.
  - Enables **horizontal scaling** — more servers can be added seamlessly.
  - Improves **fault tolerance** and resilience.
- **Cluster Configuration**: A secondary HAProxy runs in parallel to provide failover capability, avoiding a single point of failure.

### 2. Why Separate Components?

Dividing the architecture into distinct roles brings multiple advantages:

- **Web Server**:
  - Specialized in handling HTTP/HTTPS requests and static files.
  - Offloads processing from application servers.

- **Application Server**:
  - Focuses on backend logic like user sessions, API handling, and dynamic content.
  - Can scale independently based on workload.

- **Database Server**:
  - Stores structured data and handles all read/write queries.
  - Separation improves data security and simplifies backups or replication setups.

---

✅ **Conclusion**  
This modular design improves scalability, makes troubleshooting easier, and ensures each part of the system can grow or be maintained independently.

