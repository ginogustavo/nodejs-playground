# Node features

- asynchronous
- non-blocking
- single-thread
- event-driven

## Synchronous example

Syncrhonous lines run one after another
asynchronous, non blocking model -> Node can continue to do other things, like run everthing down below while it's waiting for those 2 seconds to pass

![image](https://user-images.githubusercontent.com/5447557/151668201-91fb3fd6-eb6e-473f-beca-4f53800735a5.png)

## Asynchronous example

[image 2]

setTimeout() is not a javascript function, Node.js creates an implementation of the setTimeout using C++ and provides it.

When used setTimeout(), it registers an event in Node APIs, that is an event callback pair.

- event: to wait 2 seconds
- callback: the function to run

another example: callback pair:

- event: wait for DB request to complete
- callback: do something with the data

### Non-Blocking:

When setTimeout() is executed, a new event gets registered in **Node APIs** (and start waiting the milliseconds).
Call Stack (single-threated) is not blocked and can continue and the Node API can manage the events asynchronoulsly.

The in Node.js can be single threaded, but it uses other threads in C++ behind the scenes to manage events. That's why this is not blocking the original call stack running.

Now, for the callback pairs to executes, it uses the Event loop: callback queue.

### Callback queue:

maintain a list of all of the callback functions that are ready to get executed.

When a given event is done, e.g. the milliseconds in the timer is complete, the function we defined in the callback pair will be added in the Queue.

In the Queue, the ones that are ready to get executed, it needs to be added to the Call Stack, where functions go to run.

### EVENT LOOP (EL):

EL looks at the "Call Stack" and also the "Callback Queue"

If the Call Stack is empty, it's going to run items from the Callback Queue

So, Call Stack continues, once main() gets completed and removed from the Stack,

it's empty.
In synchronous program code this is when app finishes. However in Asysnchronous pro