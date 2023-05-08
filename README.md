Download Link: https://assignmentchef.com/product/solved-ser334-module-9-shortest-job-first-scheduling
<br>
<h1>[pdf-embedder url="https://assignmentchef.com/wp-content/uploads/2022/12/ser334_unit9_hw02.pdf"]</h1>
<h1>Shortest-Job-First Scheduling</h1>
Summary: In this homework, you will be implement a program that simulates the Shortest-Job-First Scheduling algorithms.
<h2>1 Background</h2>
In this assignment you will write a program that simulates using the shortest-job- rst (SJF) algorithm(s) to pick which processes should be scheduled in what order. In the material, SJF is introduced as the basic idea that if we know how long each of the set of active processes that wants to run will take, then we can order them by their size, and then execute them in that order to minimize waiting and completion time. Later, this algorithm was extended with a live algorithm that predicted how long a process would take given it’s previous history of execution.

This document is separated into four sections: Background, Requirements, Data File, and Submission. You have almost nished reading the Background section already. In Requirements, we will discuss what is expected of you in this homework. In Data File, we discuss the format of the simulation data. Lastly, Submission discusses how your source code should be submitted on BlackBoard.
<h2>2 Requirements</h2>
In this assignment you will write a program that simulates scheduling processes. Your program needs to implement the SJF and SJF live algorithms. Your simulation should be divided into ’ticks’ where each process is scheduled (based on <em>t<sub>n </sub></em>or <em>τ<sub>n </sub></em>values), and allowed to execute. The values of <em>t<sub>n </sub></em>represent the CPU burst times required by a process over it’s lifetime. Note that a tick is di erent than the current time. A tick is simulating running a batch of processes, whereas time globally increases as each process in a batch runs. The rst few ticks of the SJF on the processes given in Data File section are illustrated below:

For the live algorithm, you should rely on <em>τ </em>each iteration not <em>t<sub>n</sub></em>which is the actual time the process takes in that tick and a value unknown to the algorithm (it is trying to guess it!). At the end of each simulation, display the turnaround and waiting times. For the live algorithm, also compute the “estimation error” which is the sum of the absolute di erences between each <em>τ<sub>n </sub></em>and <em>t<sub>n</sub></em>. When you calculate turnaround and waiting times, do so with respect to the beginning of the latest tick. That is, don’t include waiting on the previous ticks since the process was executing at those times and is only waiting within the current tick. Sample output:

==Shortest -Job-First==

Simulating 0th tick of processes @ time 0:

Process 0 took 6.

Process 1 took 13.

Simulating 1th tick of processes @ time 19:

Process 0 took 4.

Process 1 took 13.

Simulating 2th tick of processes @ time 36:

Process 0 took 6.

Process 1 took 13.

Simulating 3th tick of processes @ time 55:

Process 0 took 4.

Process 1 took 13.

Simulating 4th tick of processes @ time 72:

Process 1 took 6.

Process 0 took 13.

Simulating 5th tick of processes @ time 91:

Process 1 took 4.

Process 0 took 13.

Simulating 6th tick of processes @ time 108:

Process 1 took 6.

Process 0 took 13.

Simulating 7th tick of processes @ time 127:

Process 1 took 4.

Process 0 took 13.

Turnaround time: 184 Waiting time: 40

==Shortest -Job-First Live==

Simulating 0th tick of processes @ time 0:

Process 0 was estimated for 10 and took 6.

Process 1 was estimated for 10 and took 13.

Simulating 1th tick of processes @ time 19: Process 0 was estimated for 8 and took 4.

Process 1 was estimated for 11 and took 13.

Simulating 2th tick of processes @ time 36: Process 0 was estimated for 6 and took 6.

Process 1 was estimated for 12 and took 13.

Simulating 3th tick of processes @ time 55: Process 0 was estimated for 6 and took 4.

Process 1 was estimated for 12 and took 13.

Simulating 4th tick of processes @ time 72:

Process 0 was estimated for 5 and took 13. Process 1 was estimated for 12 and took 6. Simulating 5th tick of processes @ time 91:

Process 0 was estimated for 9 and took 13. Process 1 was estimated for 9 and took 4.

Simulating 6th tick of processes @ time 108:

Process 1 was estimated for 6 and took 6.

Process 0 was estimated for 11 and took 13.

Simulating 7th tick of processes @ time 127:

Process 1 was estimated for 6 and took 4.

Process 0 was estimated for 12 and took 13. Turnaround time: 200 Waiting time: 56

Estimation Error: 45

As an worked out example computation for SJF, turnaround time is computed as: (6+19) + (4+17) + (6+19) + (4+17) + (6+19) + (4+17) + (6+19) + (4+17)=184 and waiting time is: (0+6) + (0+4) + (0+6) + (0+4) + (0+6) + (0+4) + (0+6) + (0+4) = 40.
<ul>
 	<li>Speci c Requirements:</li>
</ul>
Read data on processes to simulate from local data le that is passed in as the rst command line argument. [5 points]

Read data with dynamical memory allocation to support any number of processes and time steps.

[8 points]

Simulate the shortest-job- rst algorithm:

∗ Simulates and displays each tick. [3 points]

∗ Executes SJF algorithm on the set of processes. [4 points]

∗ Displays turnaround and waiting times. [3 points] Simulate the shortest-job- rst live algorithm:

∗ Simulates and displays each tick. [3 points]

∗ Executes SJF live algorithm on the set of processes. [6 points]

∗ Displays turnaround, waiting times, estimation error. [4 points]
<h2>3 Data File</h2>
Your program is required to read in a text le which contains a description of a set of processes which will be simulated. The rst line lists the number of simulation ticks , the second the number of processes. After that, processes are listed in sequence from 0 to the number indicated. Each process number is followed by a tau value, a alpha value, and data for actual run times equal to the number of simulation ticks. All numbers but alpha are integers.

In the case of the normal algorithm, you should ignore the <em>τ </em>and <em>α </em>information, and only use the <em>t<sub>n</sub></em>data that represents for a speci c simulation tick, how much time that process wants. For the live algorithm, you should rely on <em>τ</em>each iteration, not <em>t<sub>n</sub></em>which is the actual time the process takes in that tick and a value unknown to the algorithm (it is trying to guess it). A sample data le is attached to this assignment (not the one we will test with) and an annotated version is shown below. Be aware that the input le we use to grade will most likely use a di erent number of ticks and processes. You will need to use malloc to allocate the correct memory based on the parameters given in the le.

8;ticks. see blackboard for the version of this file you need to support

2;process count

0;start of process 0

10;process 0 tau

.5;process 0 alpha

6;t_0 for process 0

4;t_1 for process 0

6;…

4

13

13

13

13;t_7 for process 0 1;start of process 1

10;process 1 tau

.5;process 1 alpha

13;t_0 for process 1

13;t_1 for process 1 13;…

13

6

4

6

4;t_7 for process 1