
#Multi-Level Feedback Queue Scheduling


1. Processes that are ready for execution reside in one of the 32 run queues
2. Each run queue contains processes of 4 adjacent priorities (prio/4 =run queue)
3. At every context switch, the process at the head of the highest priority queueis chosen for execution


4 After each quantum, (which is set to 0.1s) the currently running process is context switched out.
5 What happens to the process after context switch?
  The scheduler removes the process from the head of its original queue
  adjusts its priority (if needed)
  places it at the end of the queue that it belongs to
6. The run queues are then rescanned for the highest priority queue that contains a runnable process.
