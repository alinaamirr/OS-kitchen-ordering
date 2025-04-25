

## Overview

This project demonstrates how to prevent **deadlock**, **starvation**, and ensure **mutual exclusion** in concurrent systems using threads and semaphores. Two separate simulations are included:

- The **Dining Philosophers Problem** models the challenge of shared chopstick (resource) usage among philosophers.
- The **Chef Resource Management Simulation** models chefs acquiring two kitchen resources to cook, ensuring fair access and recovery from potential deadlocks.

---

## Programs Included

### 1. Dining Philosophers Problem

A classical synchronization problem involving five philosophers sitting around a table, each alternating between thinking and eating. The program ensures:

- Mutual exclusion when accessing shared resources (forks).
- No deadlock or starvation.
- Philosophers pick up forks only if both left and right are available.

**Key Concepts:**

- POSIX threads
- Semaphores
- State tracking (`THINKING`, `HUNGRY`, `EATING`)

### 2. Chef Resource Management Simulation

Ten chefs each require two specific kitchen resources (e.g., Stove, Knife, Chopping Board) to cook. Each chef:

- Tries to acquire resources in a consistent order to avoid deadlock.
- Uses `sem_wait`, `sem_post`, and `sem_timedwait` for time-bound resource acquisition.
- Waits and retries if unable to acquire both resources to prevent indefinite blocking.

**Resources Simulated:**
- Knife
- Stove
- Chopping Board
- Cooking Pot
- Vegetables

**Deadlock Prevention Techniques:**
- Ordered resource acquisition
- Timeout with retry logic (`sem_timedwait`)
- Fair release and reacquisition

---

## Technologies Used

- C Programming Language
- POSIX Threads (`pthread`)
- Semaphores (`sem_t`)
- `<unistd.h>` for sleep functions
- `<errno.h>` for error handling
- `<time.h>` for timeout mechanisms

---

## How to Compile

Use `gcc` to compile either of the programs:

```bash
gcc -pthread -o dining_philosophers philosophers.c
gcc -pthread -o chef_simulation chefs.c
