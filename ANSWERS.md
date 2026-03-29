# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer: A thread is a smaller unit of execution that operates inside a process and shares its memory, whereas a process is an independent program with its own memory and system resources. The creation and management of processes is more time-consuming and resource-intensive. On the other hand, threads enable quicker task-to-task communication and are lightweight. Because they make the simulation more effective and simpler to build, threads were used in this assignment. Separate procedures would needlessly increase overhead and complexity.**

[Write your answer here. Consider: What is a process? What is a thread? How do they differ in terms of memory, resources, creation overhead? Why are threads more suitable for this simulation?]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer: In Round-Robin scheduling, if a process does not finish within its assigned time quantum, it is moved to the end of the ready queue. This allows other processes to execute before it gets another turn. The process will continue execution later when it reaches the front of the queue again. This behavior ensures fairness and prevents any process from monopolizing the CPU.
**

[Write your answer here. Describe the specific behavior - where does the process go? When does it run again? Give an example from your actual program output showing a process that was re-queued.]

Example from my output:
```
 P1 completed quantum 4000ms │ Overall progress: [██████████░░░░░░░░░░] 52%
Remaining time: 3668ms
 P1 yields CPU for context switch
 P1 added to ready queue │ Burst time: 7668ms | priority: 3
```

**Explanation of example:
In this instance, process P1 ceded the CPU since it failed to finish execution inside the allotted time period. As seen in the output, it was then positioned at the end of the ready queue. This implies that other processes will run before P1 is given another chance. It will pick up where it left off when its turn arrives again. This conduct guarantees equitable scheduling for every process.**
[Explain what's happening in the output snippet you pasted]

---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer: Depending on how it is constructed and carried out, the thread that represents process P1 travels through multiple states throughout the simulation. Every state corresponds to a certain phase of the thread lifetime. Method calls such as start(), run(), and sleep() cause these transitions. We can plainly see how P1 shifts between these states by following the code. This aids in comprehending the behavior of threads within a scheduling system.**

[Write your answer here. For each state, explain when P1 enters that state during the simulation. Use your understanding of the code to trace through the lifecycle.]

1. **New**: P1 is in the New state when the thread object is created using `new Thread(process)` but before calling the start() method.

2. **Runnable**: P1 enters the Runnable state when `Thread.start()` is called, making it ready to be scheduled by the CPU.

3. **Running**: P1 is in the Running state when the CPU begins executing the `run()` method of the process.

4. **Waiting**: P1 enters the Waiting state when `Thread.sleep()` is called during execution to simulate processing time.

5. **Terminated**: P1 reaches the Terminated state after finishing its execution when its remaining time becomes zero.
   
---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: [Web Server ]

**Description**: 
Several client requests, such loading webpages or handling user activities, are sent to a web server simultaneously. 
A different thread can be used to handle each request. To guarantee a positive customer experience, these requests must be handled promptly.

**Why Round-Robin works well here**: 
Every request is given an equal amount of CPU time thanks to round-robin scheduling. It keeps one request from blocking others, particularly if processing takes longer. This keeps the server operating smoothly and enhances system responsiveness. Additionally, it guarantees that every incoming request will be executed consistently.

### Example 2: [Operating System CPU Scheduling]

**Description**: 
Operating systems manage multiple running programs and background tasks simultaneously. Each program or process requires CPU time to execute. The system must decide how to distribute CPU time among them efficiently.

**Why Round-Robin works well here**: 
Round-Robin scheduling ensures fairness among all running applications by assigning a predetermined time quantum to each process. In time-sharing systems with numerous active users, it is particularly helpful. This strategy guarantees that every process has an opportunity to run and prevents starvation. Additionally, it enhances interactive apps' responsiveness.

---

## Summary

**Key concepts I understood through these questions:**
1. The distinction between processes and threads, as well as the reasons why threads perform better in scheduling simulations.  
2. Round-Robin scheduling provides process fairness by utilizing time quantum.  
3. A thread's lifecycle and the various phases it goes through while being executed.
     
**Concepts I need to study more:**
1. How to safely manage shared resources and synchronize threads.  
2. The comparison between Round-Robin and advanced scheduling methods.
