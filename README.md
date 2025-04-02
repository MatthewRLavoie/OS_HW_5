# OS_HW_5
Matthew Lavoie

Part 1
Sources
https://www.geeksforgeeks.org/difference-between-priority-inversion-and-priority-inheritance/
https://www.baeldung.com/cs/priority-inversion
https://www.geeksforgeeks.org/priority-inheritance-protocol-pip-in-synchronization/

Q1. Priority inversion occurs in this system when a high-priority thread (T1) is blocked because a low priority thread (T2) holds a shared resource lock, but a medium priority thread (T3) prevents T2 from finishing and releasing the lock. At time = 0, T2 starts executing and acquires the lock. At time = 1, T1 arrives and attempts to access the shared resource but gets blocked since T2 holds the lock. At time = 2, T3 arrives and, due to having a higher priority, it go's before T2 , delaying T2’s execution. This causes T1, the highest priority thread, to be indirectly delayed by T3, which does not even need the shared resource. Without intervention, T3 could keep preempting T2, preventing it from completing and releasing the lock, leading to indefinite blocking of T1.

PIP Time
Time = 0: T2 starts executing and acquires the lock.
Time = 1: T1 arrives and requests the lock but gets blocked since T2 holds it.
Time = 2: T3 arrives and would normally preempt T2, but under PIP, T2 inherits T1’s priority and continues execution without being preempted.
Time = 3: Nothing.
Time = 4: Nothing.
Time = 5: T2 finishes execution and releases the lock.
Time = 5: T1 starts executing and acquires the lock.
Time = 6: Nothing.
Time = 7: Nothing.
Time = 8: Nothing.
Time = 9: T1 finishes execution and releases the lock.
Time = 9: T3, which had been waiting, executes.
Time = 10: Nothing.
Time = 11: Nothing.
Time = 12: T3 finsishes.

Total time: 12 units


PPP Time

Time = 0: T2 starts executing and acquires the lock.
Time = 1: T1 arrives and requests the lock but gets blocked since T2 holds it.
Time = 2: T3 arrives but cannot preempt T2 because the priority ceiling mechanism prevents it from running while T2 holds the resource.
Time = 3: Nothing.
Time = 4: Nothing.
Time = 5: T2 finishes execution and releases the lock.
Time = 5: T1 starts executing and acquires the lock.
Time = 6: Nothing.
Time = 7: Nothing.
Time = 8: Nothing.
Time = 9: T1 finishes execution and releases the lock.
Time = 9: T3, which had been waiting, executes.
Time = 10: Nothing.
Time = 11: Nothing.
Time = 12: T3 finsishes.

Total time: 12 units


Q2.

1. In PIP, T2 starts at time = 0 and runs uninterrupted due to priority inheritance until time = 5. In PPP, T2 starts at time = 0 and runs uninterrupted due to the priority ceiling, completing at time = 5.
2. T2 completes at time = 5 in both protocols, so neither protocol is faster for T2.
3. In both PIP and PPP, the total execution time is 12 units.
4. T1 does not experience priority inversion in either, becuase in PIP T2 inherits T1’s priority and is not preempted by T3, while in PPP because the priority ceiling prevents T3 from preempting T2.
5. In PIP, since T2 inherits T1's priority when T1 requests the resource, T3 cannot preempt T2 even though it arrives at time = 2. As a result, T3 is forced to wait until both T2 and T1 finish before it executes. In PPP, when T2 acquires the lock at time = 0, the system sets the priority ceiling to priority 1 (matching T1, the highest-priority thread that can use the resource). This prevents T3 (priority 2) from preempting T2 when it arrives at time = 2. As a result, T3 is forced to wait until both T2 and T1 finish before it executes.


Part 2

A-bit operating system, B pages, C of RAM

a: Use A
b: log2(C)
c: log2(B)
d: Virtual Adress - Offset
e: Physical Adress - Offset


32-bit operating system, 4-KB pages, 1 GB of RAM

ia: 32 bits
ib: log2(1 GB) = log2(2^30) = 30 bits
ic: log2(4 KB) = log2(2^12) = 12 bits
id: 32 - 12 = 20 bits
ie: 30 - 12 = 18 bits


32-bit operating system, 16-KB pages, 2 GB of RAM

iia: 32 bits
iib: log2(2 GB) = log2(2^31) = 31 bits
iic: log2(16 KB) = log2(2^14) = 14 bits
iid: 32 - 14 = 18 bits
iie: 31 - 14 = 17 bits


64-bit operating system, 16-KB pages, 16 GB of RAM

iiia:64 bits
iiib: log2(16 GB) = log2(2^34) = 34 bits
iiic: log2(16 KB) = log2(2^14) = 14 bits
iiid: 64 - 14 = 50 bits
iiie: 34 - 14 = 20 bits
