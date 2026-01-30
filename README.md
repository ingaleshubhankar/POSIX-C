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

# Table of Contect

## 1.[POSIX and Threads](https://github.com/ingaleshubhankar/POSIX-C/tree/main/POSIX%20and%20Threads#posix-and-threads)
- 1.1 [What POSIX means for threading](https://github.com/ingaleshubhankar/POSIX-C/blob/main/POSIX%20and%20Threads/What%20POSIX%20means%20for%20threading.md)
- 1.2 [Background and motivation](https://github.com/ingaleshubhankar/POSIX-C/blob/main/POSIX%20and%20Threads/Background%20and%20motivation.md)
- 1.3 [Why pthread exists](https://github.com/ingaleshubhankar/POSIX-C/blob/main/POSIX%20and%20Threads/Why%20pthread%20exists.md)
- 1.4 [The POSIX–Unix contract](https://github.com/ingaleshubhankar/POSIX-C/blob/main/POSIX%20and%20Threads/The%20POSIX%20Unix%20contract.md)

## 2. [The pthread Library](https://github.com/ingaleshubhankar/POSIX-C/tree/main/The%20pthread%20Library#the-pthread-library)
- 2.1 [What pthread really is](https://github.com/ingaleshubhankar/POSIX-C/blob/main/The%20pthread%20Library/What%20is%20pthread%20library.md)
- 2.2 [Thread lifecycle](https://github.com/ingaleshubhankar/POSIX-C/blob/main/The%20pthread%20Library/Thread%20lifecycle.md)
- 2.3 [Thread identity and execution model](https://github.com/ingaleshubhankar/POSIX-C/blob/main/The%20pthread%20Library/Thread%20identity%20and%20execution%20model.md)

## 3. [Thread Creation and Synchronization](https://github.com/ingaleshubhankar/POSIX-C/tree/main/Thread%20Creation%20and%20Synchronization#thread-creation-and-synchronization)
- 3.1 [pthread_create()](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Thread%20Creation%20and%20Synchronization/Create%20Thread.md)
- 3.2 [pthread_exit()](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Thread%20Creation%20and%20Synchronization/Exit%20Thread.md)
- 3.3 [pthread_join()](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Thread%20Creation%20and%20Synchronization/Join%20Thread.md)
- 3.4 [Relationship between create, exit, and join](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Thread%20Creation%20and%20Synchronization/Relationship%20between%20create%2C%20exit%2C%20and%20join.md)

## 4. [Race Conditions and Shared Memory](https://github.com/ingaleshubhankar/POSIX-C/tree/main/Race%20Conditions%20and%20Shared%20Memory#race-conditions-and-shared-memory)
- 4.1 [Why races occur](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Race%20Conditions%20and%20Shared%20Memory/Why%20races%20occur.md)
- 4.2 [Memory visibility basics](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Race%20Conditions%20and%20Shared%20Memory/Memory%20visibility%20basics.md)
- 4.3 [Why synchronization is required](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Race%20Conditions%20and%20Shared%20Memory/Why%20synchronization%20is%20required.md)

## 5. [pthread Mutex](https://github.com/ingaleshubhankar/POSIX-C/tree/main/pthread%20Mutex#pthread-mutex)
- 5.1 [Why mutex exists](https://github.com/ingaleshubhankar/POSIX-C/blob/main/pthread%20Mutex/Why%20mutex%20exists.md)
- 5.2 [Lock/unlock semantics](https://github.com/ingaleshubhankar/POSIX-C/blob/main/pthread%20Mutex/Lock%20unlock%20semantics.md)
- 5.3 [Common mistakes](https://github.com/ingaleshubhankar/POSIX-C/blob/main/pthread%20Mutex/Common%20mistakes.md)

## 6. [pthread Semaphore](https://github.com/ingaleshubhankar/POSIX-C/tree/main/pthread%20Semaphore#pthread-semaphore)
- 6.1 [Counting vs binary](https://github.com/ingaleshubhankar/POSIX-C/blob/main/pthread%20Semaphore/Counting%20vs%20binary.md)
- 6.2 [When semaphore is needed](https://github.com/ingaleshubhankar/POSIX-C/blob/main/pthread%20Semaphore/When%20semaphore%20is%20needed.md)

## 7. [Mutex vs Semaphore](https://github.com/ingaleshubhankar/POSIX-C/tree/main/Mutex%20vs%20Semaphore#mutex-vs-semaphore)
- 7.1 [Differences in intent](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Mutex%20vs%20Semaphore/Differences%20in%20intent.md)
- 7.2 [When to use which](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Mutex%20vs%20Semaphore/When%20to%20use%20which.md)
- 7.3 [Combining them safely](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Mutex%20vs%20Semaphore/Combining%20them%20safely.md)

## 8. [POSIX Threads and C++](https://github.com/ingaleshubhankar/POSIX-C/tree/main/POSIX%20Threads%20and%20C%2B%2B#posix-threads-and-c)
- 8.1 [Why C++ introduced std::thread](https://github.com/ingaleshubhankar/POSIX-C/blob/main/POSIX%20Threads%20and%20C%2B%2B/Why%20C%2B%2B%20introduced%20thread.md)
- 8.2 [How it maps to pthread](https://github.com/ingaleshubhankar/POSIX-C/blob/main/POSIX%20Threads%20and%20C%2B%2B/How%20it%20maps%20to%20pthread.md)
- 8.3 [Why POSIX knowledge still matters](https://github.com/ingaleshubhankar/POSIX-C/blob/main/POSIX%20Threads%20and%20C%2B%2B/Why%20POSIX%20knowledge%20still%20matters.md)

## 9. [Additional Topics](https://github.com/ingaleshubhankar/POSIX-C/tree/main/Additional%20Topics#additional-topics)
- 9.1 [Detach vs join](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Additional%20Topics/Detach%20vs%20join.md)
- 9.2 [Thread-local storage](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Additional%20Topics/Thread-local%20storage.md)
- 9.3 [Thread cancellation](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Additional%20Topics/Thread%20cancellation.md)
- 9.4 [zombi threads](https://github.com/ingaleshubhankar/POSIX-C/blob/main/Additional%20Topics/zombi%20threads.md)
<br>
<br>
<br>
<br>

---
