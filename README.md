# HelloWorldApp
1. Clone the Repository
     git clone https://github.com/your-username/HelloWorldApp.git
     cd HelloWorldApp
   
3. Build and Run the Application Locally (Without Docker)
     dotnet restore
     dotnet build
     dotnet run
   
5. Build the Docker Image
   rom the project root directory (where the Dockerfile is located), run:
   docker build -t helloworldapp .
   
6. Run the Docker Container
   After the image is built, run it using Docker:
   docker run -d -p 8080:8080 --name helloworldapp_container helloworldapp
   
7. Deploy the Application to Kubernetes
   Push the Docker Image to Minikube’s Docker (if using Minikube)
        eval $(minikube -p minikube docker-env)
   Then, rebuild the Docker image so it’s available in Minikube:
        docker build -t helloworldapp .

8. Apply the Deployment:
   kubectl apply -f deployment.yaml
9. Apply the Service:
   kubectl apply -f service.yaml

10. Verify the Deployment
    Check that your pods are running:
         kubectl get pods
11. Expose the Application (for Minikube)
    Get the Minikube IP:
         minikube ip
    Access the application at:
         curl http://<minikube-ip>:30007
12. Expose the Application (in localhost)
    run:
         kubectl port-forward service/helloworldapp-service 5001:80
    access on: localhost:5001
13. Scale the Application
    To scale the number of running pods, use the following command:
         kubectl scale --replicas=5 deployment/helloworldapp-deployment
    
15. Health Checks (Bonus)
    visit: curl http://<minikube-ip>:30007/health

    
    



   

   

      
   
   


   
   
