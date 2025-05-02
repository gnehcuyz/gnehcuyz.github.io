---
ShowToc: false  
title: Distributed File System Simulator  
date: 2024-10-28  
draft: false  
summary: Built a fault-tolerant distributed file system using the actor model and ring-based topology.  
math: true  
---

## Description

This project simulates a fault-tolerant distributed file system using the actor model. The system includes a Directory Service and multiple File Servers connected in a ring. Clients send commands to upload and download files, and the Directory Service assigns files to servers using a hash function. Files are automatically replicated to improve reliability, and if a server fails, the system continues working by forwarding the request to the next server in the ring. 

## Tech Stack  
- erlang  
- Shell scripting

## Contributions  
- Implemented the Directory Service to manage file locations and ring connections.  
- Built File Server actors to handle file storage, replication, and fault handling.  
- Developed the Client actor to process upload, download, and query commands.  
- Ensured system could handle server crashes by forwarding requests to active neighbors.  
- Tested the system under different failure scenarios to confirm reliability.
