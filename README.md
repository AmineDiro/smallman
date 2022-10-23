# SmallMan - Container in GO

Inspired from : https://www.infoq.com/articles/build-a-container-golang/

## NOTES : Building a container :

### Namespaces :

Provide isolation.

- **PID**: Gives the appearance of isolated process tree in the container
- **MNT**: gives the process's contained their _own mount table_. With `pivot_root` syscall we can have containerized filesystems (ie run ubuntu, alpine ..)
- **NET**: Created an isolated network stack . Communication is possbile creating virtual link between the network namespaces
- **UTS**: own view on hostname and domain name => Good for DNS
- **IPC**: isolates inter process communication mechanisms such as IP message queues
- **USER**: Maps the UID of a process to a different set of UIDS an GID on the host. Good for security : We can map the uid0 (ie root) of the container to an unpriviledged user

### Cgroups:

For resources management : Collect a set of process and apply **limits** to them.

### Layed Filesystems:

For efficiency. Basically leverages linux's copy on write mechanism. layered filesystems amount to optimising the call to create a copy of the root filesystem for each container.


## TO Add
- [ ] Setting cgroups
- [ ] Root FS management to cache filesystem images
