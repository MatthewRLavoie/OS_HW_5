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
1. 
2. 
3.
4.
5.

Part 2




ia
ib
ic
id
ie
iia
iib
iic
iid
iie
iiia
iiib
iiic
iiid
iiie
