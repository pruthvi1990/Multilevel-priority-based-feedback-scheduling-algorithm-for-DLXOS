
#Multi-Level Feedback Queue Scheduling


>Unlike multilevel queue scheduling algorithm where processes are permanently assigned to a queue, multilevel feedback queue scheduling allows a process to move between queues. This movement is facilitated by the characteristic of the CPU burst of the process. If a process uses too much CPU time, it will be moved to a lower-priority queue. This scheme leaves I/O-bound and interactive processes in the higher priority queues. In addition, a process that waits too long in a lower-priority queue may be moved to a higher priority queue. This form of aging also helps to prevent starvation of certain lower priority processes.

##Algorithm

Multiple FIFO queues are used and the operation is as follows:

    A new process is inserted at the end (tail) of the top-level FIFO queue.
    At some stage the process reaches the head of the queue and is assigned the CPU.
    If the process is completed within the time quantum of the given queue, it leaves the system.
    If the process voluntarily relinquishes control of the CPU, it leaves the queuing network, and when the process becomes ready again it is inserted at the tail of the same queue which it relinquished earlier.
    If the process uses all the quantum time, it is pre-empted and inserted at the end of the next lower level queue. This next lower level queue will have a time quantum which is more than that of the previous higher level queue.
    This scheme will continue until the process completes or it reaches the base level queue.

            At the base level queue the processes circulate in round robin fashion until they complete and leave the system. Processes in the base level queue can also be scheduled on a first come first served basis.[2]
            Optionally, if a process blocks for I/O, it is 'promoted' one level, and placed at the end of the next-higher queue. This allows I/O bound processes to be favored by the scheduler and allows processes to 'escape' the base level queue.

For scheduling, the scheduler always start picking up processes from the head of the highest level queue. If the highest level queue has become empty, then only will the scheduler take up a process from the next lower level queue. The same policy is implemented for picking up in the subsequent lower level queues. Meanwhile, if a process comes into any of the higher level queues, it will preempt a process in the lower level queue.

Also, a new process is always inserted at the tail of the top level queue with the assumption that it would be a short time consuming process. Long processes will automatically sink to lower level queues based on their time consumption and interactivity level. In the multilevel feedback queue, a process is given just one chance to complete at a given queue level before it is forced down to a lower level queue.
Scheduling parameters

In general, a multilevel feedback queue scheduler is defined by the following parameters:[2]

    The number of queues.
    The scheduling algorithm for each queue which can be different from FIFO.
    The method used to determine when to promote a process to a higher priority queue.
    The method used to determine when to demote a process to a lower priority queue.
    The method used to determine which queue a process will enter when that process needs service.

