**AKS Cluster with 3-Tier Application Deployment
**

**Overview**
This project sets up an AKS cluster using Terraform and deploys a 3-tier application (frontend, backend, and database) using Helm charts. The application is based on the example-voting-app by Codefresh, with modifications to suit the deployment environment.

1. Build AKS Cluster

The main.tf file sets up a resource group and an AKS cluster with a single node pool containing 3 nodes of the Standard_DS2_v2 size. The network profile is configured with specific IP ranges.

2. Deploy 3-Tier Application
Deploy the 3-tier application using Helm charts. The application consists of a frontend, backend, and database, based on the example-voting-app reference on this link https://github.com/codefresh-io/example-voting-app/tree/master/example-voting-app/charts.

**Pod Status
**
All pods for the different components (postgresql, redis, result, vote, worker) are running without any restarts, indicating stable and healthy deployments.
Service Configuration

PostgreSQL: The PostgreSQL service does not have an external IP assigned, which is expected if it's meant to be internal and accessed only by other components within the cluster.
Redis: Similar to PostgreSQL, the Redis service does not have an external IP, indicating internal usage.
Result: This service has an external IP (4.156.105.89) and is accessible via port 32320.
Vote: This service also has an external IP (51.8.216.120) and is accessible via port 30186.

**Accessing the Services
**

Result Service: You can access the results of the voting application by navigating to http://4.156.105.89:80 in your web browser.
Vote Service: The voting interface can be accessed via http://51.8.216.120:80.
