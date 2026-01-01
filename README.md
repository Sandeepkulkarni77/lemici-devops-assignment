# Lemici DevOps Internship Assignment

# Part-1: Version Control  
Task-1
- Repository was set up using SSH authentication. 
- SSH keys were generated locally and the public key was added to GitHub.  
- Repository was cloned using the SSH URL.
- Git operations work without username/password, confirming SSH setup.

Task-2
git fetch vs git pull 
git fetch:
- Downloads new data from remote repo(commits,files).
- Does not change you local branch,updates only remote tracking branch. Ex- origin/main. 
- Provides more control, you can inspect the changes before deciding to integrate them. 
- Does not cause conflicts. 
- Use when you want to review the updates safely without integrating it to your current work or simply check what others have been doing. 

git pull: 
- Download and then merges new data into your current working branch. 
- Updates local branch immediately. 
- Less control, because the integration is automatic and immediate which may lead to conflicts. 
- Can cause merge conflicts if there are conflicting changes between your local and remote branch.
- Use when you want to quickly synchronize your local branch and are confident the won't cause major conflicts. (ex - working solo or on a fast paced project). 


Task-3 
How would u resolve a git merge conflict(example scenario)
- A merge conflict can occur when two branches modify the same line of a file in different ways. 
- For example, two feature branches may update the same configuration value in a shared file. 
- When the first branch is merged into the main branch, it succeeds because there is no conflict at that point.
- However, when the second branch is merged, git is unable to automatically decide which change should be kept, since both changes affect the same line,in such cases, git pauses the merge and marks the conflicting sections in the file.
- To resolve the conflict, the file is reviewed manually, the conflicting changes are analyzed, and a meaningful final version is created by keeping or combining the required changes.
- Once the file is corrected, it is staged and committed, which completes the merge process.

Task-4 
Resolving a git merge conflict (practical demonstration)
- In this task, a merge conflict was intentionally simulated using two feature branches created from the same base commit,a configuration file (config.yaml) was added to the main branch containing basic application settings, including a log_level parameter.
- Two branches, feature-A and feature-B, were created from the same version of the main branch.
- In feature-A, the log_level was updated to debug to represent a development or debugging requirement.
- In feature-B, the same log_level was updated to error to represent a production-focused change. Since both branches modified the same line in the same file differently, a conflict was guaranteed when merging.
- The feature-A branch was merged into main successfully because no competing change existed at that time.
- When feature-B was merged into main, Git detected conflicting changes in config.yaml and stopped the merge process.
- The conflicted file was then opened on the main branch, conflict markers were removed, and a meaningful final value was chosen for the log_level.
- After resolving the conflict, the file was staged and committed with the message “Resolved merge conflict in config.yaml”, which completed the merge process.
- This demonstrated a real-world merge conflict scenario and manual conflict resolution using git.


# Part-2: Docker & Containerization
Task-1
1. Dummy Python Web Application
- A simple Python web application was created using Flask to demonstrate Docker containerization.
- The application exposes a root endpoint (/) that returns a plain text welcome message: 
"Welcome to Sandeep's app ......"
- A health check endpoint (/health) returns a JSON response containing the application status, the current UTC timestamp, and the container hostname.
- An echo endpoint (/echo) accepts a JSON payload via a POST request and returns the same payload in the response.
- The application runs on port 5000 and binds to 0.0.0.0 so that it can be accessed from outside the Docker container.

2. Dockerfile 
- A Dockerfile was written to containerize the Flask application.
- The base image used is python:3.12-slim, which provides a lightweight Python runtime.
- A working directory /app is created inside the container to keep the application files organized.
- The requirements.txt file is copied first and dependencies are installed using pip. This helps Docker cache layers efficiently so dependencies are not reinstalled on every build.
- The application source file (app.py) is then copied into the container.
- Port 5000 is exposed since the Flask application runs on this port.
- Finally, the container is configured to start the application using the command python app.py.

Task-2 
1. Difference Between Dockerfile, Docker Image, and Docker Container
- A Dockerfile is a text file that contains instructions required to build a Docker image. It defines the base image, dependencies, configuration, and commands needed to run the application.
- A Docker image is a packaged, read-only template created from a Dockerfile. It includes the application code along with all required dependencies and runtime components.
- A Docker container is a running instance of a Docker image. Containers are isolated environments where the application actually executes.

2. Reducing docker image size
- If the initial Docker image size is large, it can be optimized using several approaches.
- A slim base image was used to reduce unnecessary packages and keep the image lightweight.
- Only required Python dependencies were installed, and pip cache was disabled using the --no-cache-dir option to avoid storing temporary files inside the image.
- The Dockerfile copies only the necessary application files, which helps keep the image small and clean.

Task-3 
1. Running the application container locally
- The Docker image was built locally using the Docker CLI.
- The container was started by mapping container port 5000 to port 5000 on the host machine.
- Once the container was running, the application was verified in the following ways:
  - The container status and logs were checked using Docker Desktop to confirm that the application started successfully.
  - The application was accessed using a web browser at http://localhost:5000.
  - A health check was performed using the /health endpoint, which returned a valid JSON response including status, timestamp, and container hostname.


2. Screenshots

• Git operations
<img width="1919" height="1021" alt="Screenshot 2025-12-31 230604" src="https://github.com/user-attachments/assets/4fe97048-c28b-4fa3-8183-8ecd383e33ba" />

• Docker Desktop showing running container
<img width="1561" height="289" alt="Screenshot 2025-12-31 230728" src="https://github.com/user-attachments/assets/dbe0f927-af94-40d1-9ec5-0617b7eb059a" />

• Application running inside Docker container
<img width="1907" height="970" alt="Screenshot 2025-12-31 230819" src="https://github.com/user-attachments/assets/ceb396bb-a802-4fdb-8a34-1e6de45a7688" />

 
# Part-3: Kubernetes (EKS Basics) 
Task-1 
Difference between Pod, Deployment, and Service: 
- Pod: A Pod is the smallest deployable unit in Kubernetes,it encapsulates one or more tightly coupled containers that share the same network namespace and storage,and it represents a single instance of an application.
- Deployment: A Deployment is a higher-level Kubernetes object that provides declarative management of applications,it manages ReplicaSets, which in turn ensure the desired number of Pods are running,deployments handle rolling updates, rollbacks, scaling, and self-healing automatically.
- A Service is an abstraction that exposes a logical set of Pods using labels and selectors,since Pods are ephemeral and can change IPs, a service provides a stable IP address and DNS name to reliably access an application. 

Why do we need EKS instead of running Kubernetes on VMs?
- Amazon EKS removes the operational burden of managing the Kubernetes control plane. 
- AWS manages critical components like the API server, etcd, upgrades, high availability, and security patches. 
- In self-managed Kubernetes on VMs, teams must handle cluster setup, control-plane failures, upgrades, backups, and security themselves.
- With EKS, teams can focus on deploying and scaling applications while benefiting from deep integration with AWS services like IAM, VPC, CloudWatch, and Load Balancers.

Task-2: 
- A LoadBalancer Service is defined to expose the application externally.
- This is a dummy configuration provided as YAML only and was not deployed to an actual Kubernetes cluster, as deployment was not required for this assignment.

# Part-4: CI/CD Pipeline 
- A GitHub Actions workflow is implemented to automate the CI process.
- The pipeline triggers on every push to the main branch and performs the following steps:
   - Checks out the source code
   - Builds the Docker image for the application
   - Runs basic tests (simulated for this assignment)
   - Simulates pushing the Docker image to DockerHub

#Workflow execution: 
The screenshot below shows a successful execution of the GitHub Actions pipeline:
<img width="1429" height="579" alt="Screenshot 2026-01-01 145247" src="https://github.com/user-attachments/assets/767fb501-d38e-42b8-871b-ef6e4b2ed718" />

Deploying to Kubernetes:
- If this pipeline were extended to deploy to Kubernetes, additional steps would be added to:
  - Authenticate with the Kubernetes cluster (ex-AWS EKS)
  - Apply Kubernetes manifests using `kubectl`
  - Perform rolling updates and verify deployment health


#Deploying to Kubernetes
- If this pipeline were extended to deploy to Kubernetes, additional steps would be added to:
  - Authenticate with the Kubernetes cluster (ex-AWS EKS)
  - Apply Kubernetes manifests using `kubectl`
  - Perform rolling updates and verify deployment health


# Part-5: Monitoring & Logs
Task1-Explain the difference between metrics, logs, and traces? 
1- metrics: 
- Metrics are numerical values collected over time,they help us understand the overall health and performance of a system. 
ex-cpu usaged. memory usage, request count, error rate
- Metrics are useful when we want to see trends and detect issues early,like high cpu usage or sudden spikes in traffic.

2- logs: 
- Logs are detailed records of events that happen inside an application or system,they usually contain messages like errors, warnings, or info logs.
ex-application startup logs, error messages, request/respone count. 
- Logs are mainly used for debugging because they show what exactly happened and where it failed.

3- Traces: 
- Traces track the flow of a request across multiple services,they help us understand how much time is spent in each service when a request travels through a system.
- Traces are useful in microservices architectures where one request touches multiple services.

Task2-Debugging a Crashing Kubernetes Pod 
- If a k8s pod, i would debug it step by step as follows: 
- check pod status 
kubectl get pods
this tells me whether the pod is in CrashLoopBackOff, Error, or Pending state.

- describe the pod
kubectl describe pod <pod-name> 
this shows detailed information such as events, restart count, and possible reasons like image pull failure or resource limits.

- check container logs
kubectl logs <pod-name>
logs usually give the exact error message that caused the crash.

- check resource usage if needed 
kubectl top pod <pod-name>
this helps identify if the pod is crashing due to high CPU or memory usage.

- exec into the pod if it's running 
kubectl exec -it <pod-name> -- /bin/sh
this helps verify environment variables, files, or configurations inside the container.


Task3-Monitoring Tools for AWS EKS
- For monitoring an EKS cluster, I would suggest the following tools:
- prometheus: 
Used for collecting metrics from Kubernetes and applications.
Works well with Kubernetes and is widely adopted.

- grafana: 
Used for visualizing metrics collected by Prometheus.
Helps create dashboards for CPU, memory, pod status, etc.

- AWS cloudWatc: 
Native AWS service.
Useful for collecting logs, metrics, and setting alarms.
Integrates easily with EKS.

- ELK Stack (elasticsearch, logstash, kibana):
Used for centralized logging.
Helps search and analyze logs efficiently.

- Using these tools together gives good visibility into cluster health, application performance, and logs for debugging.

# Part-6: Problem solving scenario 

- To set up a new microservice on AWS EKS, I would follow the bellow steps: 

1. Source Code Management: 
  - The application code is hosted on GitHub.
  - Developers work on feature branches and raise pull requests.
  - The main branch is protected and used for deployments.

2. Containerization: 
  - I would clone the repository locally to understand and test the application.
  - A Dockerfile and dependency file (such as requirements.txt) would be added to containerize the application.
  - The Docker image would be built and tested locally to ensure the application runs correctly.
  - The image would then be pushed to a container registry such as DockerHub or Amazon ECR.

3. CI/CD Automation: 
- A CI/CD pipeline (using GitHub Actions or Jenkins) would be configured.
- On every merge to the main branch, the pipeline would:
  - Build the Docker image
  - Run basic tests
  - Push the image to the container registry
  - Deploy the updated image to AWS EKS using Kubernetes manifests.

4. Deployment to EKS:
- Kubernetes Deployment and Service YAML files would be used to deploy the application to the EKS cluster.
- Rolling updates would ensure zero downtime during deployments.

5. Logging and Monitoring:
- Application logs would be written to stdout/stderr so Kubernetes can capture them.
- Logs would be collected using tools like CloudWatch or ELK stack and made accessible to the development team.
- This allows developers to debug issues without directly accessing containers.

6. Overall, this approach ensures automated deployments, scalability, and visibility into application behavior while minimizing manual intervention.




