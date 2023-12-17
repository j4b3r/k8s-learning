**K8S Health Probe Sample Yaml File**  
These are some examples of how health probes work on K8S. Before starting, you need to create /data/ on your nodes.  
We use a volume (/data/ on the host) and mount it on pods (as /test-vol/). This deployment uses nginx with 6 replicas.   

**liveness Probe**  
In this file, we use /test-vol/liveness as a liveness probe to check if this file exists.  
If the file does not exist, the pod is considered not live, and Kubernetes tries to restart the pod.  
First, deploy this pod, and you will notice that the pod status shows many restarts. After that,  
run `touch /data/liveness` on your nodes. Once you do that, Kubernetes considers the pod as live and stops restarting it.  
Remember to use `kubectl describe pod PODNAME` to view logs.
