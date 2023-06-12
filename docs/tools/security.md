# Security

## Introduction

This documentation provides a comprehensive overview of our company's server architecture, utilizing WireGuard for server communication, Docker Swarm for service orchestration, and Transport Layer Security (TLS) for secure external connections. This infrastructure incorporates state-of-the-art technologies to ensure high availability, security, and scalability.

## Server Architecture

Our architecture consists of three servers interconnected via a VPN, establishing a robust platform for running distributed services. This setup facilitates high resilience, distributing the workload across multiple nodes, allowing the system to remain functional even if one of the servers fails.

The servers communicate via WireGuard, a secure, modern, and efficient VPN protocol. Docker Swarm manages the services running on these servers, ensuring they function efficiently and reliably. External connections to these services are secured using TLS, guaranteeing that all transmitted data remains confidential and secure.

## WireGuard

WireGuard is an open-source VPN designed as a general-purpose VPN, suitable for various circumstances, from embedded interfaces to supercomputers. It uses state-of-the-art cryptography like the Noise protocol framework, Curve25519, ChaCha20, Poly1305, BLAKE2, SipHash24, HKDF, ensuring top-level security.

Noteworthy security features of WireGuard include:

1. **Cryptographically Sound:** WireGuard leverages cutting-edge cryptographic protocols to ensure secure, fast, and reliable connections.
   
2. **Shorter Keys:** WireGuard employs shorter keys compared to other VPN protocols, leading to reduced complexity and faster key generation.
   
3. **Perfect Forward Secrecy:** WireGuard supports Perfect Forward Secrecy (PFS), securing past communication even if a private key is compromised because it uses ephemeral keys for each connection.
   
4. **Denial of Service (DoS) Resistance:** WireGuard's design minimizes data exchanged during connection establishment, reducing the potential for DoS attacks.
   
5. **IP Address Hiding:** By default, WireGuard does not include the originating IP address in the data packets, hiding the traffic's source.

## Docker Swarm

Docker Swarm, a container orchestration tool by Docker, Inc., allows us to manage a cluster of servers as a single virtual server. It enables easy deployment, scalability, and high availability of applications.

Here are key points about our Docker Swarm setup:

1. **Services and Stacks:** We organize related services into stacks, each with its own `docker-compose.yml` file, facilitating easy deployment and management of groups of related services.

2. **Load Balancing:** Docker Swarm natively supports load balancing of requests between different instances of a service.

3. **Service Discovery:** Docker's internal DNS server allows services within the Swarm to communicate with each other by name, eliminating the need to hard-code IP addresses.

4. **Scaling:** We can easily scale up a service by increasing the number of instances (replicas). Docker Swarm will distribute the new instances across the Swarm nodes.

5. **Rolling Updates and Rollbacks:** Docker Swarm supports rolling updates, allowing us to deploy a new version of a service without downtime. If something goes wrong, we can roll back to the previous version.

Docker Swarm also offers various security features:

1. **TLS for Nodes:** Docker Swarm uses mutual TLS for all node communication, ensuring all communication between nodes is encrypted and authenticated.

2. **Security Scanning and Signed Images:** Docker Security Scanning and Docker Content Trust identify and mitigate vulnerabilities in the application layers of our Docker images, and prevent tampered images from being deployed.

3. **Service Isolation:** Docker Swarm enforces network isolation, so each service deployed on the swarm can only communicate with other services via explicitly defined network paths.

4. **Secret Management:** Docker Swarm provides secure storage of secrets that can be used by services. Secrets are encrypted during transit and at rest, and only shared with services that specifically request them.

Docker Swarm's orchestration capabilities ensure high availability, which is a crucial aspect of our overall security strategy:

1. **Rolling Updates:** Docker Swarm performs rolling updates to services, where new versions of services are gradually rolled out. This not only ensures continuous availability of services, but also means that security updates can be applied without any downtime. If an update fails, Docker Swarm automatically rolls back, reducing the risk of exposure to vulnerabilities.

2. **Service Rescheduling:** In the event of a node becoming unavailable, Docker Swarm automatically reschedules the services running on that node to other available nodes. This functionality ensures continuous service availability, reducing the potential for attackers to exploit periods of downtime.

3. **Load Balancing:** Docker Swarm has built-in load balancing that distributes service requests evenly among all instances. This not only improves overall service reliability but also aids in mitigating Distributed Denial of Service (DDoS) attacks by distributing traffic.

4. **Scaling:** Docker Swarm allows for horizontal scaling, where additional instances of a service can be quickly started to handle increased load. This means that in the event of a sudden traffic surge, perhaps due to a DDoS attack, new instances can be deployed rapidly to maintain service availability. These new instances are automatically balanced across the nodes in the swarm, helping to manage the load and maintain uptime.

## Transport Layer Security (TLS)

Transport Layer Security (TLS) secures connections over a network by encrypting the data sent between an app and its server. We use Let's Encrypt to generate free TLS certificates for each of our services, which are automatically renewed before expiry, ensuring our connections remain secure always.

Here are a few key points about our TLS setup:

1. **Automated Certificate Management:** We use the Certbot tool to automatically issue and renew Let's Encrypt certificates.

2. **Strict Transport Security:** We use the HTTP Strict Transport Security (HSTS) policy to instruct browsers to always use HTTPS, eliminating the risk of unsecured connections.

3. **Forward Secrecy:** Our TLS configuration supports forward secrecy, meaning that if a session key is compromised, it can't be used to decrypt past or future sessions.

## Conclusion

Our company's server architecture is designed to provide a secure, robust, and scalable platform for running our services. With WireGuard, Docker Swarm, and TLS at the heart of our infrastructure, we can maintain high availability and security, ensuring our system is resilient to failures, prepared for scaling as needed, and robust against potential security threats.

Should you have any questions or need further clarification on any part of the system, please don't hesitate to contact the IT department. We're here to help!

---

## Read More

- [Docker Secrets Management](https://docs.docker.com/engine/swarm/secrets/)
- [Docker Security Best Practices](https://docs.docker.com/develop/security-best-practices/)
- [Guide to Docker Swarm Security](https://sweetcode.io/guide-swarm-security/)
- [How Swarm Mode Works - PKI](https://docs.docker.com/engine/swarm/how-swarm-mode-works/pki/)
- [Docker Swarm Mode Overview](https://docs.docker.com/engine/swarm/)

