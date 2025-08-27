# 🚀 Kubernetes (K8s) Commands Cheat Sheet

---

## 🔹 1. Cluster Info & Configuration
```bash
kubectl version                  # Show client & server version
kubectl cluster-info             # Show cluster master & services
kubectl config view              # Show kubeconfig
kubectl config current-context   # Show current context
kubectl config use-context <ctx> # Switch context
kubectl get nodes                # List all nodes
kubectl describe node <node>     # Show node details
🔹 2. Get Resources
bash
Copy code
kubectl get pods                         # List all pods in default namespace
kubectl get pods -o wide                 # Pods with more details
kubectl get all                          # Get all resources
kubectl get namespaces                   # List namespaces
kubectl get svc                          # List services
kubectl get deployments                  # List deployments
kubectl get rs                           # List replica sets
kubectl get configmap                    # List config maps
kubectl get secret                       # List secrets
kubectl get ingress                      # List ingress rules
🔹 3. Describe Resources
bash
Copy code
kubectl describe pod <pod-name>           # Pod details
kubectl describe deployment <deploy>      # Deployment details
kubectl describe service <svc-name>       # Service details
🔹 4. Create Resources
bash
Copy code
kubectl create namespace dev
kubectl create deployment nginx --image=nginx
kubectl create service clusterip mysvc --tcp=80:80
kubectl create configmap myconfig --from-literal=key=value
kubectl create secret generic mysecret --from-literal=user=admin
🔹 5. Apply / Update
bash
Copy code
kubectl apply -f file.yaml    # Apply config (create or update)
kubectl edit deployment <dep> # Edit running deployment
🔹 6. Delete Resources
bash
Copy code
kubectl delete pod <pod-name>
kubectl delete deployment <dep>
kubectl delete service <svc>
kubectl delete namespace dev
kubectl delete -f file.yaml
🔹 7. Logs & Debugging
bash
Copy code
kubectl logs <pod>                   # Show logs of pod
kubectl logs <pod> -c <container>    # Logs of specific container
kubectl exec -it <pod> -- /bin/bash  # Get shell access inside pod
kubectl describe pod <pod>           # Pod debug info
kubectl top pod                      # Resource usage of pods
kubectl top node                     # Resource usage of nodes
🔹 8. Scale & Rollout
bash
Copy code
kubectl scale deployment <dep> --replicas=3
kubectl rollout status deployment <dep>
kubectl rollout history deployment <dep>
kubectl rollout undo deployment <dep>
🔹 9. Port Forwarding & Services
bash
Copy code
kubectl port-forward pod/<pod> 8080:80
kubectl expose deployment nginx --type=NodePort --port=80
🔹 10. Namespace Usage
bash
Copy code
kubectl get pods --all-namespaces
kubectl get pods -n kube-system
kubectl create ns test
kubectl delete ns test
🔹 11. Dry Run & Manifest Generation
bash
Copy code
kubectl run nginx --image=nginx --dry-run=client -o yaml
kubectl create deployment myapp --image=nginx --dry-run=client -o yaml > deploy.yaml
🔹 12. Resource Management
bash
Copy code
kubectl get quota
kubectl get limits
kubectl cordon <node>     # Mark node unschedulable
kubectl drain <node>      # Safely evict pods from node
kubectl uncordon <node>   # Mark node schedulable
🔹 13. Events
bash
Copy code
kubectl get events --sort-by=.metadata.creationTimestamp
🔥 Common Shortcuts
bash
Copy code
kubectl get po     # same as: kubectl get pods
kubectl get svc    # same as: kubectl get services
kubectl get deploy # same as: kubectl get deployments
