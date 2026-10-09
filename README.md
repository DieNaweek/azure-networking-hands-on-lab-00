# azure-networking-hands-on-lab-00
Hands-on Azure networking project implementing infrastructure deployments, traffic routing, Layer 4 load balancing, Layer 7 Application Gateway, backend pools, health probes, and path-based routing.

# AZ-104 Practical Lab — Lessons Learned

## 1. Infrastructure Deployment Using ARM Templates

### What I Did

* Loaded an existing ARM template.
* Modified the specified virtual machine size values.
* Reviewed the custom deployment settings, including the subscription, resource group and VM names.
* Deployed a virtual network, a network security group and three virtual machines.
* Encountered a deployment failure because my initial administrator password did not meet the required complexity specifications.
* Replaced it with a compliant password and successfully proceeded with deployment.

### What I Learned

* ARM templates help standardize and repeat infrastructure deployments.
* Template parameters must meet the requirements of the resources being deployed.
* When a deployment fails, checking the error details can help identify the actual cause instead of repeatedly changing unrelated settings.
* Architecture diagrams help me understand the intended infrastructure before implementing it.

## 2. Azure Load Balancer

### What I Did

* Configured a frontend public IP address.
* Configured backend pools containing virtual machine network interfaces.
* Created a TCP load-balancing rule using port 80.
* Created a TCP health probe on port 80.
* Set the idle timeout to four minutes.
* Tested the frontend public IP address in a private browser window.
* Received Hello World responses from VM0 and VM1.

### What I Learned

* A working load-balancing configuration requires the frontend, backend pool, rule and health probe to be configured appropriately.
* Testing the public IP address helped me verify application connectivity.
* Receiving responses from both virtual machines provided evidence that both could respond through the load balancer.
* Backend health and end-to-end connectivity are separate things to verify.

## 3. Azure Application Gateway

### What I Did

* Created a fourth subnet intended for the Application Gateway.
* Configured the gateway and its frontend settings.
* Configured a general backend pool with two virtual machine network interface targets.
* Configured separate Images and Video backend pools.
* Created an HTTP backend setting using port 80 and a 20-second request timeout.
* Created a routing rule with priority 10.
* Configured the /image/* path to use the Images backend pool.
* Configured the /video/* path to use the Video backend pool.
* Reviewed the gateway configuration and checked backend health.
* Observed healthy backend statuses and HTTP 200 responses.

### What I Learned

* Application Gateway operates at Layer 7 and supports routing based on HTTP request information, including URL paths.
* Backend pools identify the destinations that can receive traffic.
* Path-based routing requires the appropriate URL path map, backend pools and backend settings to be associated with the routing configuration.
* HTTP 200 responses indicate successful HTTP requests.
* Health probes provide information about the availability of backend targets.

## 4. Overall Practical Lessons

* Practical deployment experience helps me connect Azure concepts with real configurations.
* Reviewing errors and correcting the underlying issue is an important troubleshooting skill.
* Screenshots provide evidence of the configuration and testing work completed.
* I should verify resource health and connectivity instead of assuming a successful configuration screen means everything works.
* I must never publish administrator passwords, credentials or other secrets in a public repository.
