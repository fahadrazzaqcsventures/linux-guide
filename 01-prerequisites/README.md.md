# Prerequisites

## How does internet works?

1. **The Internet = a global network of networks**

    The Internet is basically millions of computers and devices connected together around the world, communicating through standardized rules called protocols (mainly TCP/IP).

2. **How data moves (in packets)**

    When you send a message, open a website, or stream a video:
    * Your data is broken into small chunks called packets.
    * Each packet is labeled with:
        * __Source address__ (your device’s IP)
        * __Destination address__ (the server’s IP)
    * These packets travel independently across routers and networks until they reach the destination.
    * The destination reassembles the packets into the original message.

3. **Your device connects through an ISP**

    * Your phone or computer connects to a router (Wi-Fi or cable).
    * The router connects to your Internet Service Provider (ISP) — like PTCL, StormFiber, or Nayatel in Pakistan.
    * The ISP sends your data onto the backbone of the Internet, which is a global system of high-speed fiber-optic cables.
  
4. **DNS – the Internet’s “phonebook”**

    * When you type a website like `www.google.com`, your computer:
    * Asks a DNS server to find the corresponding IP address (like 142.250.190.78).
    * Then it connects to that IP address to reach Google’s servers.
  
5. **Client–Server model**

    Most of the Internet works using this model:

    * __Client__: your browser or app (makes a request)
    * __Server__: a powerful computer that hosts data or applications (sends back a response)

    __Example:__

    You → request `www.youtube.com` → DNS resolves IP → your browser connects → YouTube’s server sends HTML, CSS, video, etc.

6. **Security and HTTPS**

    Modern sites use HTTPS (HTTP + SSL/TLS) — it encrypts data between you and the server, protecting it from snooping or tampering.

7. **Protocols make it all work**

    Some key Internet protocols:
    * HTTP/HTTPS – web traffic
    * FTP/SFTP – file transfer
    * SMTP/IMAP – email
    * SSH – secure remote access
    * TCP/IP – foundation of all communication

## What is a Server?

A **server** is simply a **computer or program** that **provides services or resources** to other computers — called **clients** — over a **network** (like the Internet or a local network).

### 1. Basic Idea

- A **client** sends a **request** (for example, your browser asking for a web page).  
- A **server** listens, processes that request, and sends back a **response** (like the HTML page).  

This is called the **client-server model** — it’s how most of the Internet works.

**Example:**

Client (Browser) → "GET /index.html" → Web Server → sends → index.html

### 2. Types of Servers

| Server Type | Purpose | Example Software |
|--------------|----------|------------------|
| **Web Server** | Serves web pages | NGINX, Apache |
| **Application Server** | Runs backend app logic | Node.js, Django, Spring Boot |
| **Database Server** | Stores & retrieves data | MySQL, PostgreSQL, MongoDB |
| **File Server** | Stores and shares files | Samba, NFS |
| **DNS Server** | Resolves domain names | BIND, Route53 |
| **Mail Server** | Handles emails | Postfix, Exim |
| **Proxy / Load Balancer** | Distributes or filters traffic | HAProxy, NGINX, AWS ELB |

### 3. Physical vs Virtual Servers

| Type | Description | Example |
|------|--------------|----------|
| **Physical Server** | A real machine in a data center | Dell PowerEdge, HP ProLiant |
| **Virtual Server (VM)** | A software-based server running inside a physical one | AWS EC2, Azure VM |
| **Containerized Server** | Lightweight, portable server environment | Docker container running NGINX |

In modern DevOps, most servers are **virtual** or **containerized** — they’re created and destroyed dynamically using **cloud platforms** or **Kubernetes**.

### 4. Server Characteristics

- **Always on** (or highly available)  
- **Listens on specific ports** (e.g., 80 for HTTP, 443 for HTTPS)  
- **Configured for performance & security**  
- **Can handle multiple client requests simultaneously**

### 5. From a DevOps Perspective

As a DevOps engineer, your job often involves:

- **Setting up servers** (on AWS, Azure, GCP, or bare metal)  
- **Configuring services** (web, app, DB servers)  
- **Automating provisioning** (using Terraform, Ansible, or CloudFormation)  
- **Monitoring & scaling** servers  
- **Securing** them with firewalls, IAM, and encryption  

### Example: A Simple Web Server Setup

User → Browser → Internet → NGINX Web Server → Node.js App → Database

Here:

- **NGINX** acts as the **web/reverse proxy server**.  
- **Node.js** acts as the **application server**.  
- **PostgreSQL** is the **database server**.

### In Short

> A **server** is a machine (physical or virtual) that **listens for requests**, **processes them**, and **returns responses** — forming the backbone of all online services.

## Difference between web server & application server?

### Web Server
- **Purpose:** Handles **HTTP requests** from clients (browsers) and serves **static content** — like HTML, CSS, JS, and images.  
- **Examples:** **NGINX**, **Apache**, **Caddy**  
- **Key Role:**  
  - Accepts requests on port 80/443  
  - Delivers static files quickly  
  - Can forward (reverse proxy) dynamic requests to an application server  

**Think:** “Serves static files and routes traffic.”

### Application Server
- **Purpose:** Runs the **backend application logic** — processes data, connects to databases, and generates dynamic responses.  
- **Examples:** **Node.js**, **Django**, **Spring Boot**, **Flask**  
- **Key Role:**  
  - Executes business logic  
  - Interacts with databases  
  - Returns dynamic content (JSON, HTML templates, etc.)

**Think:** “Runs your app’s code and logic.”

### How They Work Together

Browser → Web Server (NGINX) → Application Server (Node.js / Flask) → Database

- The **web server** manages incoming requests and serves static files.  
- The **application server** handles the app logic and returns dynamic responses.

### In Short

> **Web Server = Serves static files + routes requests**  
> **Application Server = Runs backend logic + generates dynamic content**

## Types of applications?

| **Type** | **Runs On** | **Description** | **Examples** |
|-----------|--------------|-----------------|---------------|
| **Web Application** | Web Browser | Accessed via a browser using HTTP/HTTPS. Usually built with frontend + backend technologies. | Gmail, YouTube, LinkedIn |
| **Desktop Application** | Operating System (Windows, macOS, Linux) | Installed on a computer and runs locally on the OS. | VS Code, Photoshop, Word |
| **Mobile Application** | Mobile OS (Android, iOS) | Installed from app stores and runs natively on smartphones or tablets. | WhatsApp, Instagram, Spotify |
| **Cloud / SaaS Application** | Cloud Infrastructure | Hosted in the cloud and accessed online. Users don’t manage servers or installs. | Google Docs, Slack, Notion |
| **Command-Line (CLI) Application** | Terminal / Shell Environment | Runs in the command-line interface, often for system or DevOps tasks. | Git, Docker CLI, AWS CLI |
| **Microservices Application** | Containers / Cloud Environment | Built as multiple small independent services communicating via APIs. | Netflix, Amazon backend |
| **Hybrid / Cross-Platform Application** | Multiple Platforms (Web, Mobile, Desktop) | One codebase that works across different environments. | Discord, Slack, Flutter apps |

## What are standalone applications?

A **standalone application** is a **self-contained program** that runs **entirely on a single computer** — it does **not require a network connection or external server** to function.

### Key Characteristics
- Installed **locally** on the user’s system.  
- Runs **independently** — all logic, data, and processing happen on the same machine.  
- **No Internet or backend server** required to operate.  
- Often stores data **locally** (e.g., on disk or a local database).

### Examples

| **Application** | **Description** |
|------------------|-----------------|
| **VLC Media Player** | Plays videos locally without needing the Internet. |
| **MS Paint / Photoshop** | Edits images using local processing. |
| **Calculator / Notepad** | Basic desktop tools that don’t rely on servers. |
| **VS Code (Offline Mode)** | Runs and edits files without network dependency. |

---

### Standalone vs. Other Application Types

| **Type** | **Runs On** | **Network Required?** | **Example** |
|-----------|--------------|-----------------------|--------------|
| **Standalone App** | Local computer | ❌ No | VLC, Calculator |
| **Web App** | Browser (online) | ✅ Yes | Gmail, YouTube |
| **Client-Server App** | Client + Backend Server | ✅ Yes | Banking System, Games |
| **Cloud / SaaS App** | Cloud Infrastructure | ✅ Yes | Google Docs, Slack |

### In Short
> A **standalone application** is a **self-contained program** that runs on a single machine without needing Internet or server communication.

## What are web applications?

A **web application** is a **software program that runs on a web server** and is **accessed through a web browser** using the Internet.  
It doesn’t need to be installed on the user’s computer — you just open it in a browser.

**Examples:** Gmail, YouTube, Facebook, Amazon  

> **In short:** Web applications are browser-based programs that use the Internet to deliver interactive features to users.

## What is application support?

**Application Support** refers to the **ongoing maintenance, monitoring, and troubleshooting** of software applications after they are deployed and in use.  
The goal is to **ensure the application runs smoothly**, stays **available**, and meets **user needs** without interruptions.

### Key Responsibilities

- Monitor application performance and uptime.  
- Troubleshoot bugs, errors, or crashes.  
- Manage incidents and service requests.  
- Apply patches, updates, or configuration changes.  
- Coordinate with development teams for issue resolution.  
- Provide technical assistance to end users or customers.

### Example

A support engineer ensures that a company’s web app (e.g., an e-commerce site) is running 24/7, fixing errors like *“server not responding”* or *“database connection failed.”*

### In Short

> **Application Support** is about keeping applications **running efficiently and reliably**, by handling issues, updates, and user support after deployment.

## What is application maintenance?

**Application Maintenance** is the **process of updating, modifying, and improving software applications** after deployment to ensure they remain **functional, secure, and efficient** over time.

It goes beyond fixing issues — it involves **enhancing performance**, **adding new features**, and **adapting to changing business or technology needs**.

### Key Activities

- Fix bugs and errors.  
- Update libraries, dependencies, or frameworks.  
- Enhance performance and security.  
- Add new features or improve existing ones.  
- Adapt the application to new hardware or OS environments.  
- Perform preventive maintenance to avoid future issues.

### Example

A team updates a company’s payroll application to:

- Support a new tax rule.  
- Improve speed.  
- Fix reported calculation bugs.

### In Short

> **Application Maintenance** ensures that a software application stays **reliable, secure, and up to date** through continuous improvements and fixes after deployment.
