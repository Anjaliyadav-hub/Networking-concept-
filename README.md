
# Networking-concept-
<h1>Networking in Cloud Computing – Notes</h1>


<h3>1. TUN and TAP Devices</h3>

<B>TUN (Network TUNnel)</B>

Virtual network device for Layer 3 (IP packets).

Used to route IP packets between virtual networks.


<B>TAP (Network TAP)</B>

Virtual network device for Layer 2 (Ethernet frames).

Used to simulate an Ethernet network between VMs/containers.


Use in Cloud: Connect VMs, containers, or overlay networks without physical hardware.

----
<h3>2. VXLAN (Virtual Extensible LAN)</h3>

Encapsulates Layer 2 frames inside Layer 3 packets.

Allows creating overlay networks across physical networks.

ID (VXLAN Network Identifier) separates different virtual networks.

Widely used in cloud networking (OpenStack, Kubernetes).

-----
<h3>3. Flannel</h3>

Kubernetes CNI plugin for simple overlay networking.

Provides a virtual network for pods across nodes.

Typically uses VXLAN to connect pods on different nodes.

Easy to set up, suitable for small to medium clusters.

----

<h3>4. Cilium</h3>

Advanced Kubernetes CNI using eBPF (extended Berkeley Packet Filter).

Provides:

High-performance networking

Security policies

Load balancing


Works at L3/L4/L7, more efficient than Flannel.

---

<h3>5. Zero-Copy vs Packet-Copy</h3>

# Packet-Copy

Packets are copied from kernel to user space.

High CPU usage, slower performance.


# Zero-Copy

User space accesses packet memory directly.

Low CPU usage, faster network throughput.


Use case: High-speed networking in cloud, container networking.

---

<h3>6. Libvirt</h3>

API/tool to manage virtual machines.

 Networking with libvirt:

Bridged network: VM acts like physical host in LAN.

NAT network: VM shares host IP, uses NAT for external communication.

Isolated network: VMs communicate among themselves only.

---

<h3>7. Kubernetes Networking</h3>

<h3
Node: Physical or virtual machine in the cluster.>

<h3
Pod: Smallest deployable unit; has its own IP and network namespace.>

Networking handled by CNI plugins (Flannel, Cilium).

  Pod-to-Pod communication can span nodes via overlay networks (VXLAN/eBPF).

Services: Expose pods to internal/external traffic.

---

<h3>8. Summary Table</h3>

Concept	Layer	Purpose	Example/Tool

 1.TUN	L3	Route IP packets between VMs/containers	Linux TUN
 
2.TAP	L2	Connect Ethernet frames between VMs	Linux TAP

3. VXLAN	L2/L3	Overlay network across nodes	Kubernetes, OpenStack

4. Flannel	L3	Simple pod networking	Kubernetes CNI

5. Cilium	L3/L4/L7	High-performance pod networking	Kubernetes CNI

6. Zero-Copy	-	Efficient packet processing	DPDK, eBPF

7. Packet-Copy	-	Traditional packet handling	tcpdump

8. Libvirt	-	Manage VMs & virtual networks	virt-manager

9. Node (K8s)	-	Host machine in cluster	-
    
10.Pod (K8s)	-	Smallest deployable unit	-
