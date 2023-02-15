- NFS (Network File System) is a type of file system that enables computer users to access, view, store, and update files over a remote server. This remote data can be accessed by the client computer in the same way that it is accessed on the local system.
- RPCScan communicates with RPC (remote procedure call) services and checks misconfigurations on NFS shares. It lists RPC services, mountpoints,and directories accessible via NFS. It can also recursively list NFS shares. SuperEnum includes a script that performs a basic enumeration of any open port, including the NFS port (2049).

> cd RPCScan
> python3 rpc-scan.py #ip --rpc

	- **--rpc**: lists the RPC (portmapper)
	- The result appears, displaying that port 2049 is open, and the NFS service is running on it.