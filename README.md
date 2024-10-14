# UCSM —— Universal Critical Section Model

## Critical Section Types

Concurrently accessing of critical section commonly includes situations below:

- totally exclusive accessing, typically a memory block protected by a mutex;
- accessing with different priorities on query and modification, in which situation you want concurrent accessing among reading operations, but exclusive accessing when write, typically a file;
- counted accessing, which is like totally exclusive accessing but the resouces are counted, typically a thread-safe FIFO.

Developers spend thier entire life creating similiar codes for these situations with `std::evil_mutex` `pthread_whatever` `std::atomic<no_sense_type>`  (thread synchronization is not talked here, so no condition variables, no channels, no futures & promises). STL gives us primitives, which are well definded on behaviours, RAII protected, dead-lock free, but still we need to write repeat code day after day. So, introducing UCSM —— **U**niversal **C**ritical **S**ection **M**odel. You define critical sections with a type, you lock and unlock them with some verbs in a high-level view, and you do not need to think about what kind of lock you have to use.

Thing are really simple here, truly: I just plan to exsctract your daily lock-related code from your data structures, or inject into them. Further optimization may be on the agenda, but depends on my poor skills (maybe depends on yours, too).

## 