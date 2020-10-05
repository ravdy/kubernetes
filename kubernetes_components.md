## Kubernetes Components

### Master 
	kube-apiserver
	kube-scheduler
	kube-controller-manager
	etcd

### Node
	Kubelet
	kube-proxy


#### Kube-apiserver: 
	It acts as frontend for Kubernetes cluster. users, management devices and command line interfaces interactive API server to talk with Kubernetes cluster. 
	The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. The API server is the front end for the Kubernetes control plane.

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
	It comes in the picture incase cluster is running in the cloud environment. 


#### kubelet
	An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod.
