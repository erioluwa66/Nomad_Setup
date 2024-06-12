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
    
    c. Mutual TLS (mTLS): Implement mTLS for all communication within the cluster to ensure that both the server and client authenticate each other’s certificates, preventing unauthorized access.

    d. Access Control Lists (ACLs): Use ACLs to define who can access what within the Nomad cluster. ACLs provide a way to grant capabilities to tokens, which can be used to authenticate and authorize actions.

    e. Namespaces: Utilize namespaces to isolate and control access to job information within a multi-tenant cluster. Namespaces help in segregating resources and access between different teams or projects.

    f. Sentinel Policies: For enterprise users, Sentinel policies offer granular control over components such as task drivers within a cluster.

### For structuring application secrets with a secrets management system like Vault, I would consider the following approach:

    a. Namespaces or Mounts: Create namespaces or dedicated mounts for each team within the organization structure. This allows you to isolate secrets and manage access at a granular level.

    b. Secrets Engines: Use different secrets engines for different types of secrets (e.g., AWS, database, KV) and mount them at paths dedicated to each team within the organization.

    c. Policies: Define policies that grant access to specific paths within Vault. These policies should be attached to tokens or entities representing teams or services.

    d. Roles and Service Accounts: When integrating with orchestration platforms like Nomad, bind service accounts to Vault roles that define the associated access policy for the application.

    e. Dynamic Secrets: Utilize Vault’s dynamic secrets capabilities to generate short-lived, on-demand secrets for applications, reducing the risk of secret sprawl and unauthorized access.

    f. Audit Logging: Enable audit logging in Vault to keep a detailed log of all operations, which can be invaluable for security audits and real-time analysis.

    



  