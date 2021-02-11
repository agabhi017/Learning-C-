# Threads (`sf::Thread` or `std::thread`)

* Threads are simple sequences of instructions that are capable of being run in parallel to other threads or executing multiple tasks at the same time.
* For example every function has a main thread corresponding to the `main()` function. Such programs are called single-threaded-functions and adding more threads will make it multi-threaded.
* A thread instance should stay alive for as long as the funtion which is to be threaded. That is, the scope of a thread should be set decisively in order to achieve the desired task.
For instance while launching threads outside of main one should be careful about the return of the function inside which the thread is launched as that would cause the 
thread to be destructed even before the desired function is executed.
* The entry point of a thread is the function which will be run when the thread is started. It could be a non memmber or membered function or functors.
* A thread is stopped automatically when its entry point function returns. However the `wait()` function can also be called to wait for a thread to finish before running any other thread.
* Threads cannot be paused but can be put to sleep using `sf::sleep(time object)`. In such state a thread uses 0 CPU.
* Since threads run in parallel, it becomes important to manage shared resources or else the data might get corrupted. One way to do is using `sf::Mutex`.
* MUTEX stands for MUTual EXclusion. It ensures that only a single thread is able to access the code/variables that is guarded by it.
* `mutex.lock()` and `mutex.unlock()` can be used together to guard shared resources. Whenever a thread reaches a `mutex.lock()` statement, it locks the mutex and if any other thread
reaches the same statement in a different set of instructions, it has to wait until the first thread unlocks the mutex as the mutex is currently locked. 
* To avoid exception errors with mutexes that can freeze the program entirely if any mutex is not unlocked, `sf::Lock` can be used to lock and unlock the mutex.
* The `sf::Lock` has a destructor which unlocks a mutex while destructing thus avoiding instances where a mutex might remained lock forever. 
* `sf::Lock` is also convenient to use when a function has multiple return statements and hence one need not write `mutex.unlock()` several times with each return statement.
