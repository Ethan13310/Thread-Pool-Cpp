# Thread Pool
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)

C++14 thread pool implementation.

## Usage

* `thread_pool(std::size_t thread_count)` (Constructor) : Number of worker threads to instantiate.
* `push(Func &&fn, Args &&...args)` : Push a new task into the queue.
* `clear()` : Remove all pending tasks from the queue.
* `join()` : Wait all worker threads to finish. This function is called within the destructor.
* `thread_count() const` : Get the number of worker threads.
* `active_count() const` : Get the number of active worker threads (ie. the number of threads which have a task assigned).

## Example

```cpp
// Create a thread pool with 4 worker threads
thread_pool pool{ 4 };

// Add a new task into the queue
auto future{ pool.push([](double n, double p) { return std::pow(n, p); }, 2, 12) };

// Get the result from the future
std::cout << future.get() << std::endl;
```
