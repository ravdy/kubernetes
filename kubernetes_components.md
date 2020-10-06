# Kubernetes Components

### Master Components  
  kube-apiserver  
  kube-scheduler  
  kube-controller-manager  
  etcd  

### Node Components  
  Kubelet  
  kube-proxy  


#### Kube-apiserver: 
 It acts as frontend for Kubernetes cluster. users, management devices and command line interfaces interactive API server to talk with Kubernetes cluster. 


#### etcd 
 Etcd is a Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data.  
Kubernetes stores all the date related master, nodes, pods, etc in the etcd. It is distributed across the cluster. 


#### kube-scheduler
  Kube scheduler watches for newly created Pods with no assigned node, and selects a node for them to run on.

#### kube-controller-manager
  It is responsible to identify in case of node or pod failures and replace with new container or pod

Logically, each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process.

These controllers include:

`Node controller:` Responsible for noticing and responding when nodes go down.  
`Replication controller:` Responsible for maintaining the correct number of pods for every replication controller object in the system.  
`Endpoints controller:` Populates the Endpoints object (that is, joins Services & Pods).  
`Service Account & Token controllers:` Create default accounts and API access tokens for new namespaces.  


#### Cloud-controller-manager 
  It comes into the picture incase cluster is running in the cloud environment. 


#### kubelet
  An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod.

#### kube-proxy 
  kube-proxy is a network proxy that runs on each node in your cluster, implementing part of the Kubernetes Service concept.  
  kube-proxy maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster

#### Container runtime 
  it is a underlying software which is used to run our pods 
