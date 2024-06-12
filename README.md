# Kraken_assesment

A take home assisgnment from the Kraken team

## A. Setup Instructions for nomad

Follow the instructions to setup  [Nomad](https://github.com/erioluwa66/Kraken_assesment/blob/master/nomad_setup/README.md).


## B. Setup Instructions for the Microservices app

Follow the instructions to setup the [Microservices app](https://github.com/erioluwa66/Kraken_assesment/blob/master/simple-microservice/README.md).

## C.   Security

### The below include would take to secure the cluster hosts in order to prevent privilege escalation, and unauthorized network and data access:

    a. Golden Images: Create standardized machine images with pre-configured security settings, such as firewall rules, security patches, and hardened system configurations. This ensures that every instance launched from these images adheres to your security baseline.

    b. Versioning and Tracking: Use Packer to version your images and keep a history of changes. This allows you to track which security features were included in each version and rollback to a previous version if necessary, By automating the image build process, you can ensure that only the necessary packages and services are included in your images, reducing the potential attack surface.

    c. Machine language and anomaly detection - deviation from derived patterns from data over a period of time.
    
    d. Mutual TLS (mTLS): Implement mTLS for all communication within the cluster to ensure that both the server and client authenticate each other’s certificates, preventing unauthorized access.

    e. Access Control Lists (ACLs): Use ACLs to define who can access what within the Nomad cluster. ACLs provide a way to grant capabilities to tokens, which can be used to authenticate and authorize actions.

    f. Namespaces: Utilize namespaces to isolate and control access to job information within a multi-tenant cluster. Namespaces help in segregating resources and access between different teams or projects.

    g. Sentinel Policies: For enterprise users, Sentinel policies offer granular control over components such as task drivers within a cluster.

### For structuring application secrets with a secrets management system like Vault, I would consider the following approach:

    a. Namespaces or Mounts: Create namespaces or dedicated mounts for each team within the organization structure. This allows you to isolate secrets and manage access at a granular level.

    b. Secrets Engines: Use different secrets engines for different types of secrets (e.g., AWS, database, KV) and mount them at paths dedicated to each team within the organization.

    c. Policies: Define policies that grant access to specific paths within Vault. These policies should be attached to tokens or entities representing teams or services.

    d. Roles and Service Accounts: When integrating with orchestration platforms like Nomad, bind service accounts to Vault roles that define the associated access policy for the application.

    e. Dynamic Secrets: Utilize Vault’s dynamic secrets capabilities to generate short-lived, on-demand secrets for applications, reducing the risk of secret sprawl and unauthorized access.

    f. Audit Logging: Enable audit logging in Vault to keep a detailed log of all operations, which can be invaluable for security audits and real-time analysis.

## D.   Scalability

### I would scale as traffic increases by:
    a. Horizontal Scaling: Add more client nodes to the Nomad cluster to distribute the workload. Even though I started with a single-node cluster, Nomad allows me to easily add more nodes as needed.

    b. Autoscaling: Implement the Nomad Autoscaler to automatically scale the number of instances of my services based on real-time demand.

    c. Load Balancing: I would use a load balancer in front of the Nomad clients to distribute incoming traffic evenly across all available instances of the service.

    d. Resource Allocation: I would adjust resource allocation for jobs in Nomad to ensure that services have enough CPU, memory, and other resources to handle increased load.

### I would ensure reliability by:

    a. I would transition from a single-node setup to a multi-node cluster with multiple server nodes to avoid a single point of failure. This ensures that if one server node fails, others can take over.
    
    b. I would configure Nomad’s job specifications to automatically restart failed tasks and reschedule them on other nodes if necessary.

    c. Monitoring and Alerting: Implement comprehensive monitoring and alerting to detect issues early and respond quickly to traffic surges or node failures.

    d. I can also prepare disaster recovery plans, including backups and failover strategies, to quickly recover from catastrophic failures.

### Potential single points of failure currently include:
    a. Single Server Node: In a single-node cluster, the server node is a single point of failure. If it goes down, the entire cluster becomes unmanageable.

    b. Networking Issues: Network partitions or failures can isolate the Nomad node, preventing it from communicating with clients or external services.

    c. Storage: Relying on a single storage system for persistent data can be risky. Use replicated storage or cloud-based solutions to mitigate this risk.







  