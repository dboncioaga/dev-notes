## **Kubernetes Cheat Sheet**
### KUBERNETES BASICS

### Check Kubernetes Version and Cluster Info:

```bash
kubectl version --short         # Display client and server version
kubectl cluster-info            # Display cluster information
```

### Set Context for a Namespace:
```bash
kubectl get namespaces          # List all available namespaces
kubectl config set-context --current --namespace=<namespace>
```

### WORKING WITH PODS
```bash
kubectl get pods                            # List all pods in the default namespace
kubectl get pods -n <namespace>             # List pods in a specific namespace
kubectl get pods -o wide                    # Show additional details (e.g., Node, IPs)

kubectl run nginx --image=nginx             # Deploy a pod with an image
kubectl delete pod <pod_name>               # Delete a specific pod
kubectl delete pod <pod_name> --grace-period=0 --force # Delete a pod immediately

kubectl logs <pod_name>                     # Show logs of a pod
kubectl logs <pod_name> -f                  # Follow pods logs in real time
kubectl logs <pod_name> --previous          # Get logs from the previous instance of a pod
kubectl exec -it <pod_name> -- /bin/bash    # Get a shell inside a running pod
kubectl describe pod <pod_name>             # Display detailed information about a pod
kubectl top pod <pod_name>                  # Show CPU and memory usage of a pod
```

## WORKING WITH DEPLOYMENTS
### Managing Deployments:
```bash
kubectl create deployment <deployment_name> --image=<image> # Create a deployment
kubectl get deployments                                     # List all deployments
kubectl describe deployment <deployment_name>               # Describe a specific deployment
kubectl delete deployment <deployment_name>                 # Delete a specific deployment

kubectl scale deployment <deployment_name> --replicas=<number>  # Scale deployment to n replicas

kubectl set image deployment <deployment_name> <container_name>=<new_image> # Update container's image
kubectl rollout undo deployment <deployment_name>           # Roll back the last deployment
kubectl rollout status deployment <deployment_name>         # Check deployment rollout status
```

## WORKING WITH SERVICES
```bash
kubectl get services                          # List all services in the default namespace
kubectl get services -n <namespace>           # List all services in a specific namespace

kubectl expose deployment <deployment_name> --type=NodePort --port=<port> # Expose a deployment

kubectl describe service <service_name>      # Show detailed information about a service
kubectl delete service <service_name>        # Delete a specific service

## WORKING WITH CONFIGMAPS AND SECRETS
### ConfigMap Commands:
```bash
kubectl create configmap <configmap_name> --from-literal=<key>=<value> # Create a ConfigMap
kubectl create configmap <configmap_name> --from-file=<file_path>      # Create a ConfigMap from a file
kubectl get configmap <configmap_name>             # Get specific ConfigMap
kubectl describe configmap <configmap_name>        # Show detailed information about ConfigMap
kubectl delete configmap <configmap_name>          # Delete a ConfigMap
```
### Secrets Commands:
```bash
kubectl create secret generic <secret_name> --from-literal=<key>=<value> # Create a Secret
kubectl get secret <secret_name>                   # Get specific Secret
kubectl describe secret <secret_name>              # Show detailed information about the Secret
kubectl delete secret <secret_name>                # Delete a Secret
```

## WORKING WITH NODES
### Node Information:

```bash
kubectl get nodes                        # List all nodes
kubectl describe node <node_name>        # Show detailed information about a specific node
kubectl cordon <node_name>               # Mark a node as unschedulable
kubectl drain <node_name>                # Safely evict all pods from a node
kubectl uncordon <node_name>             # Mark a node as schedulable
```

## WORKING WITH HELM (PACKAGE MANAGER)
### Helm Basics:
```bash
helm repo add <repo_name> <repo_url>       # Add a chart repository
helm repo update                           # Update chart repository
helm search repo <chart_name>              # Search for a package in a repository
helm install <release_name> <chart_name>   # Install a Helm chart
helm list                                  # List all deployed Helm releases
helm uninstall <release_name>              # Uninstall a Helm release
```

## USAGE MONITORING & TROUBLESHOOTING
### Check Cluster Resources:
```bash
kubectl top nodes                             # Show CPU and memory usage for each node
kubectl top pod                               # Show CPU and memory usage for each pod

kubectl describe pod <pod_name>               # Show detailed information about a specific pod
kubectl describe service <service_name>       # Show detailed information about a specific service
kubectl describe deployment <deployment_name> # Show detailed information about a deployment

kubectl get events                            # Get recent events in the cluster
kubectl logs <pod_name>                       # View logs for a specific pod
kubectl describe <resource_type> <name>       # Display details for a specific resource
```

## USEFUL SHORTCUTS
### Apply a Configuration File:
```bash
kubectl apply -f <file_name.yaml>         # Apply changes from a YAML file
kubectl delete -f <file_name.yaml>        # Delete resources defined in a YAML file
kubectl replace -f <file_name.yaml>       # Replace resources from a YAML file
```

### Dry-run Commands:
```bash
kubectl apply -f <file_name.yaml> --dry-run=client # Simulate applying the changes
```

## ADVANCED COMMANDS
### Port Forwarding:
```bash
kubectl port-forward <pod_name> <local_port>:<remote_port>             # Forward a local port to a pod
kubectl port-forward service/<service_name> <local_port>:<remote_port> # Forward a port to a service
```

### Debug Containers:
```bash
kubectl exec -it <pod_name> -- sh                  # Open an interactive shell
kubectl cp <namespace>/<pod>:<container_path> ./destination    # Copy files from container to host
```

### Rollback to Previous Deployment:
```bash
kubectl rollout undo deployment/<deployment_name> # Roll back a deployment
```

## CLEANUP COMMANDS
### Delete Resources:
```bash
kubectl delete pod <pod_name>                # Delete a specific pod
kubectl delete deployment <deployment_name>  # Delete a specific deployment
kubectl delete service <service_name>        # Delete a specific service
kubectl delete configmap <configmap_name>    # Delete a ConfigMap
kubectl delete secret <secret_name>          # Delete a Secret
kubectl delete all --all                     # Delete all resources in the current namespace
```

## TIPS AND TRICKS
### Use Output Formatting:
```bash
kubectl get pods -o yaml                     # Output in YAML format
kubectl get pods -o json                     # Output in JSON format
```

### Enable Auto-Complete for Commands:
```bash
source <(kubectl completion bash)            # Enable bash completion
```

### Manage Contexts:
```bash
kubectl config get-contexts                  # List available contexts
kubectl config use-context <name>            # Switch to a different context
```