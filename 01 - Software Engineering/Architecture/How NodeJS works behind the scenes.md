---
type: Article
tags:
  - node
  - backend
  - insights
  - runtimes
created: 2025-10-25
updated: 19:23
---
# How NodeJS works behind the Scenes

## Summary

The article walks through Node.js’s inner mechanics, focusing on the event‑loop and its seven phases (timers, pending callbacks, idle‑prepare, poll, check, close‑callbacks, and exit). It explains how the single‑threaded JavaScript engine (V8) delegates I/O work to `libuv`'s thread pool and the OS kernel, allowing non‑blocking operations. By tracing a simple script through each phase, the author shows when timers fire, when callbacks get queued, how the poll phase handles incoming I/O, and why the process stays alive until the loop reaches the “idle‑prepare” stage. The piece demystifies why asynchronous code appears concurrent despite a single JS thread and highlights the importance of understanding each loop phase for debugging performance issues.

## Key Points

- **Event‑loop phases are deterministic** 
	- Each iteration follows a fixed order; knowing which phase a callback belongs to tells you when it will execute.
-  **`libuv` bridges JavaScript and the OS** 
	- Heavy I/O (file, network, DNS) passed off to `libuv`'s C‑level thread pool, freeing the V8 thread to continue processing JavaScript.
- **Timers vs. I/O handling** 
	- `setTimeout` callbacks run in the timers phase, while socket/read events get processed in the poll phase; mixing them can cause unexpected ordering if you assume they behave the same. 
- **"Idle‑prepare" is the hidden gatekeeper** 
	- The loop won’t exit until it reaches this phase and finds no more work, which is why a `console.log` placed after a stream’s `.end()` may appear delayed.-.
- **Callback queues are per‑phase** 
	- Pending callbacks (e.g., `process.nextTick`) run after timers but before I/O, giving them higher priority; misuse can starve the poll phase.
- **Understanding the loop aids performance tuning**
	- Identifying which phase a bottleneck sits in (e.g. long‑running CPU work blocking the poll phase) lets you restructure code or move work to worker threads.
- **Single‑thread illusion** 
	- Although JavaScript runs on one thread, the combination of `libuv`'s thread pool and the OS kernel provides true concurrency for I/O, explaining Node’s scalability.

## Subtopics

...

## Personal Thoughts

...

## Examples

...

## References

- https://www.deepintodev.com/blog/how-nodejs-works-behind-the-scenes


