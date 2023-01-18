# Event Loop

Event Loop helps to push tasks from different queues into the call stack on the basis of priority.

Important Terms:

**Execution Context (EC)**: Also called a stack frame. It has two constituents: 1) Record Variables 2) Outer EC Reference

There are three queues of importance:

1) **Task Queue or Callback Queue or Macro Task Queue**: This has all the callbacks that were asked to be run at a later point of time. For example, set timeout, set interval. It runs one task a time when the stack is completely empty, i.e, not even the main/global context.
Script execution is also a macro task

2) **Microtasks Queue: This has the highest priority**. This is the callback passed to Promise or Mutation Observer. It runs all in a single pass, even the new ones that may come while the current are running. 

3) **Animation Callback Queue** : This has middle priority(i.e., higher than callback queue). It runs one "batch" at a time, when stack frame is empty. Request Animation Frame is a part of this.


> render is a macro task


The behavior of user click and explicit click in code is different, if dealing with promises in event handlers. Because when user clicks, the call stack is already empty, whereas when click is written in code, atleast stack frame for global is present.


### Starvation

Example: If a micro task queue takes so long that it keeps the other tasks in the callback queue from executing, that will be a classic case of starvation. It is to starve a queue from executing tasks in the call stack. 

