# **System Design** 🌟

## What is System Design? 📐  
System design is the process of defining the architecture, components, interfaces, and other characteristics of a system to meet specified requirements. It involves creating a blueprint for how a system will function, ensuring it is reliable, scalable, and secure. 🔒

## What is a Software System? 💻  
A software system is a collection of software components, modules, and programs that work together to perform a specific task or set of tasks. It can be as simple as a single program or as complex as a distributed system spanning multiple devices and networks.  
**Example:** An online shopping app is a software system. It includes components for displaying product lists, processing payments, and tracking orders—all working together to provide a seamless shopping experience. 🛒

## What is a Distributed Software System? 🌐  
A distributed software system consists of multiple independent components, processes, or nodes that communicate and coordinate to achieve a common goal. Unlike a centralized system where everything runs on a single machine, a distributed system is spread across multiple machines, networks, and geographical locations.  
**Example:** Google’s search engine is a distributed system. When you search for something, your request is processed by servers located worldwide, working together to deliver results quickly. 🔍

## Challenges in Distributed Systems ⚠️  
Designing distributed systems is challenging due to several factors:  
- **Network Communication:** Ensuring components communicate effectively over networks. 📡  
- **Data Consistency:** Keeping data synchronized across multiple nodes. 📊  
- **Availability:** Ensuring the system remains operational even during failures. 🟢  
- **Fault Tolerance:** Handling failures gracefully without affecting the entire system. 🛠️  
- **Security:** Protecting the system from unauthorized access and attacks. 🔐  
**Example:** In an online banking system, if one server goes down, the system must ensure other servers can still process transactions securely and without interruption. 🏦

<div align="center">
  <img src="./images/01.jpg" alt="" width="600px"/>
</div>

## Example of a Distributed System (Based on Figure 1.1) 🖼️  
The figure illustrates a distributed system with various components. Here’s a detailed breakdown:  

1. **User Devices:** On the left, there are user devices like laptops, mobile phones, and tablets. These are the devices users interact with to send requests, such as accessing a website or app. 📱💻  
2. **Internet:** Requests travel through the internet to reach the system’s servers. 🌍  
3. **DNS Server:** The Domain Name System (DNS) server translates domain names (e.g., www.example.com) into IP addresses, directing the request to the correct destination. 🌐  
4. **CDN (Content Delivery Network):** The CDN stores static resources like images, videos, and scripts, delivering them quickly to users by caching them closer to their location. 📦  
5. **Load Balancer:** This component distributes incoming requests across multiple app servers to prevent any single server from becoming overloaded, ensuring balanced performance. ⚖️  
6. **App Servers (App Server 1, 2, 3):** These servers handle the core processing of user requests, such as retrieving product details or processing a search query. 🖥️  
7. **Proxy:** A proxy server acts as an intermediary, routing requests and adding a layer of security by filtering traffic. 🛡️  
8. **Cache:** A cache stores frequently accessed data (e.g., user profiles or product info) to reduce the load on databases and speed up response times. ⚡  
9. **DB Cluster (DB1, DB2, DB3, DB4, DB5, DB6):** This is a group of databases that store the system’s data, such as user information, product catalogs, or transaction records. Data is distributed across multiple databases for redundancy and scalability. 🗄️  
10. **Block Storage:** This storage system is used for large data, such as files, backups, or media, providing scalable and reliable storage. 📂  

### How the Distributed System Works 🔄  
- A user sends a request (e.g., opening a website) from their device.  
- The request goes through the DNS server, which resolves the domain name to an IP address.  
- The load balancer distributes the request to one of the app servers (App Server 1, 2, or 3) based on current load.  
- The app server first checks the cache for the required data; if not found, it queries the database cluster.  
- If large files are needed (e.g., images or videos), they are fetched from the block storage or CDN.  
- Finally, the processed response is sent back to the user through the same path. 🚀

---

## **More Specific System Design Definition**? 📐

System design is the process of defining the architecture, components, modules, interfaces, and interactions of a software system to meet its functional and non-functional requirements. It involves creating a blueprint that outlines how the system will be structured, implemented, and maintained. 🔧

> **Note:** The goal of system design is to create a design that is easy to understand, maintain, and extend while meeting performance, scalability, reliability, and security requirements. The design should also be flexible to accommodate future changes in requirements or the environment. 🔄

## System Design Process 🛠️

The system design process typically involves the following steps:

1. **Requirements Analysis** 📝\
   Understand and define the functional (what the system does) and non-functional (how the system performs) requirements. This step also involves analyzing read-and-write patterns to optimize the system design.\
   **Example:** For a chat app, a functional requirement is that users can send and receive messages. A non-functional requirement is that the app should handle 1 million users without slowing down. 💬
2. **High-Level Architecture Design** 🏗️\
   Define the overall structure of the system, including its components, modules, and interfaces (see Figure 1.2 for an example).\
   **Example:** For a chat app, the high-level design might include a frontend (user interface), backend servers (to handle messages), and a database (to store messages). 🌐
3. **Detailed Design** 🔍\
   Define the internal structure and behavior of each component and module, including core algorithms and interaction mechanisms between components.\
   **Example:** For a chat app, the detailed design might specify how messages are encrypted, how the backend authenticates users, and how messages are stored in the database. 🗄️
4. **User Interface Design** 🖥️\
   Design the user interface that interacts with backend services via APIs, done at a high level.\
   **Example:** For a chat app, the UI design might include a chat window, a text box for typing messages, and a send button. 📱
5. **API Design** 🌉\
   Define APIs that enable communication between the frontend and backend services.\
   **Example:** For a chat app, an API like `/sendMessage` might be created to send a user’s message to the backend. 📡
6. **Database Design** 💾\
   Design the data structures and storage mechanisms, which could range from simple file storage to relational databases (e.g., MySQL) or NoSQL databases (e.g., HBase, Cassandra).\
   **Example:** For a chat app, the database might store messages in a table with columns like `sender_id`, `receiver_id`, `message_text`, and `timestamp`. 🗃️

<div align="center">
  <img src="./images/02.jpg" alt="" width="600px"/>
</div>


## Detailed Explanation of Figure 1.2 🖼️

Figure 1.2 shows a simple high-level system design diagram of a typical web application. Let’s break it down:

1. **Frontend (Browser and Mobile App)** 📱💻\
   On the left, there are two users: one using a browser (e.g., Chrome, Firefox) and another using a mobile app. This is the frontend, the part users interact with directly. The frontend takes user input (e.g., clicking a button) and displays output (e.g., a webpage or app screen).\
   **Example:** In an online shopping app, the product list you see on your phone or browser is the frontend. 🛒
2. **APIs** 🌉\
   APIs act as a bridge between the frontend and backend, allowing them to communicate. The frontend sends requests to the backend via APIs, and the backend sends responses back.\
   **Example:** When you click “Search” in a shopping app, the frontend makes an API call like `/searchProduct` to tell the backend what you’re looking for. 🔍
3. **Internet** 🌍\
   Requests from the frontend travel through the internet to reach the backend servers.
4. **DNS Server** 🌐\
   The DNS server converts domain names (e.g., www.example.com) into IP addresses, ensuring the request reaches the correct backend server.\
   **Example:** When you type “www.amazon.com” in your browser, the DNS server converts it to an IP address pointing to Amazon’s backend servers. 📍
5. **Backend Servers** 🖥️\
   These servers handle the actual processing of requests, such as fetching data or performing calculations.\
   **Example:** In a shopping app, when you search for a product, the backend server retrieves the product details and sends them to the frontend. 🛍️
6. **Databases** 🗄️\
   Databases store all the system’s data, such as user information, product details, or orders. The backend interacts with the database to fetch or store data.\
   **Example:** When you place an order on Amazon, the backend saves your order details in the database. 📦

### How It Works 🔄

- A user performs an action on the frontend (e.g., clicking a button).
- The frontend sends a request via an API, which travels through the internet and DNS server.
- The DNS server routes the request to the appropriate backend server.
- The backend processes the request, fetching data from the database if needed, and sends a response back to the frontend via the API.
- The frontend displays the response to the user (e.g., search results or a confirmation message).

---

