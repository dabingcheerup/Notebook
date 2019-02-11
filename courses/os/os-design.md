---
description: >-
  Textbook: OS Design - The Xinu Approach (1st edition) Ch1: Introduction and
  Overview
---

# OS Design

OS provides **services**

Programs access these services by **system calls**

**System Calls** define services and  interface to these services

**Services** : 1. to understand the characteristic of the services OS provides 2. and how to use those services;

Xinu is the OS used in this book

1.4.3 Concurrent Processing

OS support concurrent processing computations which several independent computations being performed on a processor that can execute only one instruction at a time.

Xinu avoids busy waiting  by  semaphores and system calls that operate on them

Each process has:

1. local variables
2. procedure argument
3. procedure calls on the stack
4. semaphores
   1. for avoiding busy waiting
   2. mutual exclusion
5. 
