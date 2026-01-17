# Threads in C using POSIX (pthreads)
Multithreading is one of those topics that feels complicated not because it is large, But because it is usually explained in fragments. APIs come first, rules come later, and understanding is expected to appear somewhere in between.
<br>
<br>
This guide takes a different approach.
<br>
<br>
![My Image](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Pthread.png)
<br>
<br>
The guide progresses in **small**, **intentional steps**. Each section introduces one idea, explains why it exists, and only then shows the minimum code required to make it concrete. Examples are kept short and focused, and nothing is introduced without a reason. If a concept does not help you understand execution more clearly, it is left out.
<br>
<br>
This is not a performance guide, and it is not a collection of recipes. **The goal is understanding, not shortcuts**. By keeping the scope narrow and the explanations precise, **the guide aims to make multithreading feel logical rather than intimidating**.
<br>
<br>
If you already know C and want to understand how threads actually behave inside a process, this guide is meant to be read from start to finish. By the end, POSIX thread APIs should feel natural, because the behavior they express will already make sense.
<br>
<br>
## Where this guide begins

**The introduction is complete**.

From this point forward, the guide moves into the actual concepts of POSIX threads.
Topics are introduced **in indexed order**, with each index focusing on a single core idea.
Every concept builds on the previous one and is explained before any additional detail is added.

The first concept begins below.
<br>
<br>
<br>

## Table of Contect

### 1.[POSIX and Threads]
- 1.1 [What POSIX means for threading]
- 1.2 [Background and motivation]
- 1.3 [Why pthread exists]
- 1.4 [The POSIX–Unix contract]

### 2. [The pthread Library]
- 2.1 [What pthread really is]
- 2.2 [Thread lifecycle]
- 2.3 [Thread identity and execution model]

### 3. [Thread Creation and Synchronization]
- 3.1 [pthread_create()]
- 3.2 [pthread_exit()]
- 3.3 [pthread_join()]
- 3.4 [Relationship between create, exit, and join]

### 4. [Race Conditions and Shared Memory]
- 4.1 [Why races occur]
- 4.2 [Memory visibility basics]
- 4.3 [Why synchronization is required]

### 5. [pthread Mutex]
- 5.1 [Why mutex exists]
- 5.2 [Lock/unlock semantics]
- 5.3 [Common mistakes]

### 6. [pthread Semaphore]
- 6.1 [Counting vs binary]
- 6.2 [When semaphore is needed]

### 7. [Mutex vs Semaphore]
- 7.1 [Differences in intent]
- 7.2 [When to use which]
- 7.3 [Combining them safely]

### 8. [POSIX Threads and C++]
- 8.1 [Why C++ introduced std::thread]
- 8.2 [How it maps to pthread]
- 8.3 [Why POSIX knowledge still matters]

### 9. Additional Topics (Optional)
- 9.1 [Detach vs join]
- 9.2 [Thread-local storage]
- 9.3 [Thread cancellation]
- 9.4 [zombi threads]
<br>
<br>
<br>
<br>

---

