
#Multi-Level Feedback Queue Scheduling


1. Processes that are ready for execution reside in one of the 32 run queues
2. Each run queue contains processes of 4 adjacent priorities (prio/4 =run queue)
3. At every context switch, the process at the head of the highest priority queueis chosen for execution
