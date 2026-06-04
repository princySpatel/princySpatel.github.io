---
title: "OS Banker's Algorithm Simulation"
description: "An interactive, animated dashboard mapping Banker's Algorithm safety checks, fail cases, and dynamic resource allocation graphs for deadlock avoidance."
timestamp: 2026-04-05
tags: ["Operating Systems", "Python", "Streamlit", "Simulation"]
githubUrl: "https://github.com/princySpatel/banker-s-algorithm-demonstration-"

---

## Overview
Deadlock avoidance is a critical concept in Operating Systems, but tracing the matrices by hand can make the logic hard to follow. This project takes the Banker's Algorithm out of the textbook and turns it into a fully interactive, animated simulation. Built with Python and Streamlit, it allows users to configure custom processes, max needs, and resource allocations to mathematically test if a CPU scheduling state is safe.

## Visual Logic & Animation
Understanding how resources are allocated, held, and released is much easier when you can actually see the trace happen in real-time. I engineered the dashboard to generate dynamic Resource Allocation Graphs (RAG) using Graphviz. 

As the safety algorithm runs, the UI animates the state machine step-by-step:
* **Processing (Khaki):** The system actively checks if a process's remaining needs can be met by the currently available work pool.
* **Finished (Green):** The process is deemed safe, its execution completes, and its allocated resources are returned to the available pool.
* **Blocked (Red):** The process's needs exceed current availability, halting its execution to prevent a deadlock.

## Testing Edge Cases and Failures
The simulation handles complex fail cases flawlessly. Users can submit manual, on-the-fly resource requests for specific processes. The engine simulates the allocation *before* actually granting it. If the hypothetical request leads to an unsafe state, the engine rejects the allocation and outputs the exact partial sequence where the deadlock would inevitably occur.

*some of the image*

![image simulation](/images/os1.png)
![image simulation](/images/os2.png)
![image simulation](/images/os3.png)
![image simulation](/images/os4.png)
![image simulation](/images/os5.png)
