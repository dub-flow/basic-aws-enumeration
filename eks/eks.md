# AWS EKS (Elastic Kubernetes Service)

EKS is the managed Kubernetes Service of AWS.

* Kubernetes Common Misconfigurations (examples):
    - Inadequate `Pod Security Policies` (PSPs)
        - E.g. an attacker with some access to the cluster may create a new `Pod` that with a container that has `hostPath` volumes which allow accessing sensitive data from the host
        -  This is a brillant article about common Pod priv escs: https://bishopfox.com/blog/kubernetes-pod-privilege-escalation
    - `ConfigMaps` or `Secrets` that expose sensitive data and credentials to attackers
    - Insecure `Network Policies` may allow to move laterally within the cluster or exfiltrate data between `pods`
    - Unprotected `etcd` (this stored the Kubernetes configuration data) may allow attackers to gain control over the cluster
    - Exposed `kubelet` API that could allow an attacker control over worker nodes
    - ...