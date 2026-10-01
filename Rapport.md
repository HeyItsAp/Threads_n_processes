# Github link

[github.com/HeyItsAp/Threads_n_processes.git](Link to Github)

# Part 1: Threads and Processes
Process and threads are essential data-structures for computer systems to que and safely execute computer instructions. *Processes execute a program with a restricted rights, overseen by the kernel. Threads are independent and seperate sequences that execute instructions instructions*. 

The *main differences* between the two is flexability and access to system resources. Processes do not necessarily share the same memory and share resources (can be done with Shared Memory) but threads in the same process usually do. This allows for smoother and faster communication. The second difference is that (usually) processes are run at kernel-level, meaning it has access directly to important system rssources; interrupts, execptions (+ handlers) and memory. This means process are more "heavyweight", needing proper time and execution to run and terminate. Thread are depended on the parent process for those kinds of resources making it more "lightweight".

Most operating systems used a combination of threads and processes to manage complexity, for example in "Kernel Threads" where the operating system allows multiple process to run threads. Basically those threads have the same resources as the process they are running on.
- *In some cases threads are preferred to achieve responsiveness and background work*. This is done by running a parallel thread in the background. For example; When downloading a movie, the option to cancel should work. Here the cancel option is the parallel thread that handles input. A parallel process might be too slow and unnecessary use of system resources just to say "no". 
- *Process can be used for heavier system services*. Important services such as in backend server or OS daemons are usually use process. This is to securely and strictly contain a service on interruptes or failures.

For threads to work properly and to communicate effectively, most threads have a TCB, Thread Control Block. The operating system need information on the threads state, so TCB makes it into a object of some sort. The TCB contains the computation being performed by the thread (stack and registers) and the metadata about the thread . Stack and register data is to *make sure that multiple threads know each others states and so that system can properly resume a thread by invoking its registers*. Metadata for identifcation *for accurate suspenion and resuming*.

For a thread context switch to occur, a voluntary call into the thread library or an involuntary interrupt or exepction need to happen. On a voluntary call, its usually means that the thread gave up a processor, giving it to a different thread. While an involuntary one happens involuntarily and the system needs to decide to continue by restoring or run a different thread by saving and letting it go to the handler.
 





# Part 2: C program with POSIX Threads.
Given:



Function `*go` is run everytime a new thread is created. This can be idenfited in the syntax for `pthread_create`. Where the third paramater is the starting function.
In this use case, the function `*go` gets the TID (thread id) which is the iterasjon-number in the for-loop, prints it out with a message, and exits with its TID + 100.


