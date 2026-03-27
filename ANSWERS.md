# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:**
A thread is a small unit of execution inside a process that shares memory and resources, whereas a process is an independent program running on its own with its own memory space and system resources. Threads are quicker and more effective than processes, which are more costly to create and maintain. Because threads facilitate shared access to the ready queue and easier communication than processes, they were used in this assignment. Additionally, threads are better suited for mimicking scheduling methods like Round-Robin with lower overhead. This is consistent with the ideas covered in Operating System Concepts (Silberschatz et al., 10th Edition).
[Write your answer here. Consider: What is a process? What is a thread? How do they differ in terms of memory, resources, creation overhead? Why are threads more suitable for this simulation?]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum?
In Round-Robin scheduling, if a process does not complete within its assigned time quantum, it is preempted and moved back to the end of the ready queue. This ensures fairness among all processes, allowing each process to get CPU time in a cyclic order. The process will wait for its turn again until the scheduler assigns it another quantum.

Explain using an example from your program 
output.

**Your Answer:**
▶ P1 executing quantum [4000ms]
  ⚡ Quantum progress: [███████████████] 100%
  ⏸ P1 completed quantum 4000ms │ Overall progress: [████████░░░░░░░░░░░░] 41%
     Remaining time: 5550ms
  ↻ P1 yields CPU for context switch

P1 (Priority: 4) added...
Explanation of example:

From the output, process P1 did not finish execution after its time quantum (4000ms), since it still had 5550ms remaining. Therefore, it was preempted by the scheduler and placed back at the end of the ready queue, as shown when it appears again after P14. This behavior demonstrates the core concept of Round-Robin scheduling, where processes are repeatedly cycled through the CPU until they finish execution.
[Write your answer here. Describe the specific behavior - where does the process go? When does it run again? Give an example from your actual program output showing a process that was re-queued.]

Example from my output:
```
[Paste a relevant snippet from your program output here showing a process being re-queued]
```
[Explain what's happening in the output snippet you pasted]

---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**

[Write your answer here. For each state, explain when P1 enters that state during the simulation. Use your understanding of the code to trace through the lifecycle.]

1. **New**: [When is P1 in New state?]
P1 is in the New state when it is first created and added to the system:
P1 (Priority: 4) added...
At this stage, the thread has been created but has not yet started execution.
3. **Runnable**: [When does P1 become Runnable?]
After being added, P1 enters the ready queue and becomes Runnable:
 [P2 → P3 → ... → P14]
Although P1 is not shown in the queue initially (since it runs first), it is logically in the ready state waiting for CPU scheduling
5. **Running**: [When is P1 Running?]
P1 enters the Running state when it is assigned CPU time
▶ P1 executing quantum [4000ms]
Here, the thread is actively executing on the CPU.
7. **Waiting**: [When/why would P1 be Waiting?]
After finishing its quantum without completing execution, P1 is preempted
↻ P1 yields CPU for context switch
P1 (Priority: 4) added..
t this point, P1 goes back to the ready queue and waits for its next turn
│ [P3 → P4 → ... → P14 → P1]
9. **Terminated**: [When is P1 Terminated?]
Finally, P1 completes execution when its remaining time becomes zero:
▶ P1 executing quantum [1550ms]
Remaining time: 0ms
✓ P1 finished execution
At this stage, the thread enters the Terminated state and is removed from the system.
---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: Web server

**Description**: 
A web server handles multiple user requests simultaneously, where each request is treated as a separate thread.

**Why Round-Robin works well here**: 
Round-Robin ensures that each request gets a fair share of CPU time, preventing any single request from monopolizing the server. This improves responsiveness and ensures all users receive timely service.

### Example 2: 

**Description**: 
Modern operating systems manage multiple applications running at the same time, such as browsers, music players, and background services.

**Why Round-Robin works well here**: 
Round-Robin provides fairness by giving each process equal CPU time. It ensures that no application is starved and maintains system responsiveness, especially in interactive environments.

---

## Summary

**Key concepts I understood through these questions:**
1. Difference between threads and processes
 2. Behavior of Round-Robin scheduling
 3. Thread lifecycle states 

**Concepts I need to study more:**
 1. Advanced synchronization techniques
 2. Deadlocks and race conditions
