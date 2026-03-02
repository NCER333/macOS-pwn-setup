# macOS-pwn-setup
Cross-architecture Pwn setup: Colima-based x86_64 linux environment for pwn and reverse engineering on ARM64 macOS

## Prerequisites

**1. Host Tools**

Ensure you have Homebrew installed, then run:

```bash
brew install colima docker
```

**2. Initialize the x86_64 VM**
I use sshfs to share an instant directory with the main system
```bash
colima start --arch x86_64 --cpu 2 --memory 4 --mount-type sshfs 

**3. Run the container**

```bash
   docker run -d \
  --name pwn-lab \
  --cap-add=SYS_PTRACE \
  --security-opt seccomp=unconfined \
  -v "/Path/Of/Your/Shared/Directory:/pwn" \
  -w /pwn \
  ubuntu:22.04 \
  tail -f /dev/null

  docker exec -it pwn-lab /bin/bash
```

**4. Once in the shell install your tools**

   [My tools](./basic-tools)


