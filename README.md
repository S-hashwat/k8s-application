Here’s a detailed description of everything I’ve done in this task

## **Kubernetes with Minikube: Deploying an Nginx Application**

### **Objective:**
The task involved setting up a Kubernetes cluster using **Minikube**, deploying a sample Nginx application using Kubernetes manifests, 
and exposing the app using a Kubernetes Service. I also explored scaling the application and checking logs to ensure the app is functioning correctly.

### **Steps Involved:**

#### **1. Install Minikube & Kubernetes Tools:**
- **Minikube** was installed to create a local Kubernetes cluster.
- **kubectl** (Kubernetes CLI) was used to interact with the cluster, deploy applications, and manage resources.
- **Docker** was used as the driver for Minikube to run the Kubernetes components in containers on the local machine.

#### **2. Start the Minikube Cluster:**
- Minikube was started with the Docker driver to create a local Kubernetes cluster.
- A primary control plane node was created, and the cluster was initialized, with necessary Kubernetes components running (e.g., kubelet, API server).

#### **3. Create Deployment YAML (`deployment.yaml`):**
- A Kubernetes **Deployment** was defined in deployment.yaml to deploy the Nginx application. 
- The deployment included:
  - **Replicas**: The number of application instances (1 replica for simplicity).
  - **Container**: The container image used (Nginx) and the port it exposes.
  - The deployment ensures the Nginx app is running, scaling up and down if necessary.

#### **4. Create Service YAML (`service.yaml`):**
- A Kubernetes **Service** was defined in service.yaml to expose the Nginx app to external access.
- We used a **NodePort** type service, which exposed the Nginx app on a specific port on the Minikube VM’s IP address.

#### **5. Deploy the Application:**
- The deployment and service were applied using kubectl apply -f deployment.yaml -f service.yaml.
- Kubernetes automatically scheduled the Nginx pod and created the service.

#### **6. Verify the Deployment:**
- We used kubectl get pods to verify that the Nginx pod was running and in the Running state.
- kubectl get svc was used to verify that the Nginx service was created and exposed via the **NodePort**.
  
#### **7. Access the Application:**
- After exposing the service, we accessed the Nginx welcome page using the IP address and port provided by Minikube (http://192.168.49.2:30007).
- The Nginx default page was displayed, confirming the app was successfully deployed.

#### **8. Scale the Deployment:**
- We used kubectl scale to scale the deployment to 3 replicas, ensuring the application could handle more traffic by running multiple instances of the Nginx container.

#### **9. View Application Logs:**
- We used kubectl logs <pod-name> to view the logs of the Nginx pod and confirm the application was running correctly.
- The logs showed the Nginx service initializing successfully and accepting HTTP requests.

#### **10. Describe Pod Details:**
- We used kubectl describe pod <pod-name> to view detailed information about the Nginx pod, including its status, events, and resource usage.

#### **11. Tunnel the Service (Optional):**
- For Windows users with Docker as the Minikube driver, we started a tunnel to access the service locally using minikube service nginx-service.
- This opened the service URL in the browser, where the Nginx welcome page could be accessed.

---

### **Key Commands Used:**
- minikube start --driver=docker: Start the Minikube cluster using Docker.
- kubectl apply -f deployment.yaml -f service.yaml`: Deploy the application and expose it via service.
- kubectl get pods: Verify the status of the pods.
- kubectl get svc: Verify the status of the services and their assigned ports.
- kubectl logs <pod-name>: View the logs of the Nginx pod.
- kubectl describe pod <pod-name>: Get detailed information about the Nginx pod.
- kubectl scale deployment nginx-deployment --replicas=3: Scale the deployment to 3 replicas.
- minikube service nginx-service: Open the exposed service in the browser.

---

### **Outcome:**
- Successfully deployed and exposed an Nginx application on Kubernetes using Minikube.
- Verified the deployment and the service by accessing the application via the browser.
- Scaled the application from 1 replica to 3 replicas.
- Checked pod logs to confirm the application is working and examined pod details using kubectl describe.

---

### **Conclusion:**
This task demonstrated the basics of deploying and managing applications in Kubernetes using Minikube, a tool for local Kubernetes clusters.
The application was successfully deployed, exposed, scaled, and managed through Kubernetes manifests and kubectl commands.
