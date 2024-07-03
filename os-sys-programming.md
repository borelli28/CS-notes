# CS162: Operating Systems and Systems Programming - UC Berkley, John Kubiatowicz


### Lecture 1 - Intro
Operating systems
- Provide consistent abstractions to applications
- Manage sharing of resources among multiple applications

Building blocks:
- Processes
- Threads, Concurrency, Scheduling, Coordination
- Address spaces
- Protection, isolation, sharing, security
- Communication, protocols
- Persistent storage, transactions, consistency, resilience
- Interfaces to all devices

OS Basics:
- Hardware:
    1) Processor
    2) Memory
    3) Storage
    4) Networks
- OS:
    1) Threads
    2) Address spaces
    3) Files
    4) Sockets
- Process: Execution environment wit restricted rights provided by the OS
- Compiled program
    - System libraries

### Lecture 2
The OS abstracts underlying hardware to help tame complexity
- Processor -> thread
- Memory -> address space
- Disks, SSDs -> files
- Networks -> sockets
- Machines -> processes

Four fundamental OS concepts
- Thread: Execution context
	- Fully describes program state
	- Program counter, registers, execution flags, stack
- Address space
	- Set of memory addresses accessible to program(for read/write)
	- May be distinct from memory space of the physical machine
- Process: An instance of a running program
	- Protected address space
- Dual mode operation/protection
	- Kernel mode, and user mode
	- Only the "system" has the ability to access certain resources
	- Combined with translation, isolates programs from each other and the OS from programs

Thread Control Block(TCB): Holds contents of registers when thread is not running. Use on multithreaded processes, during context switch

### Lecture 3 - Abstractions: Threads and Processes
Thread: A single unique execution context
- Thread purpose: OS needs to handle multiple things at once(MTAO)
- Threads are a unit of concurrency provided by the OS
- Each thread can represent one thing or one task

Running threads concurrently: Scheduler(kernel) is free to run threads in any order, by breaking threads into chunks and running them in the most efficient way possible.

Thread states
- RUNNING
- READY: Eligible to run, but not currently running
- BLOCKED: Ineligible to run

pthreads: OS library API for threads(semi standardise for all OS's
- pthread_create: Creates a thread, and the returns is an implicit call to pthread_exit
- pthread_exit: Terminates the thread
- pthread_join: Suspends execution of the calling thread until the target thread terminates

Shared vs per-thread state
- Shared state: State shared by every thread
	- Heap
	- Global variables
	- Code
- Per-thread state: State unique for each thread
	- TCB: Thread control block
		- Stack information
		- Saved registers
		- Thread metadata
	- Stack: Stack holds temporary results, permits recursive execution(push each function on execution to stack)

pthreads lock
- pthread_mutex_init: Initialize lock
- pthread_mutex_lock: Grab a lock
- pthread_mutex_unlock: Release the lock

Bootstrapping: Processes are created by other processes. The first process is created by the kernel and its called the "init" process.

Process management APIs
- exit: terminate a process
- fork: copy the current process
- exec: change the program being run by the current process
- wait: wait for a process to finish
- kill: send a signal to another process
- sigaction: set handlers for signals

### Lecture 4 - Files and I/O
Semaphore: A kind of generalized lock. A semaphore has a non-negative integer value and supports the following two operations:
- P() or down(): Atomic operation that waits for semaphore to become positive, then decrements it by 1
- V() or up(): Atomic operation that increments the semaphore by 1, waking up a waiting P, if any
- Called a binary semaphore or mutex:
	inital value of semaphore = 1;
	semaphore.down();
		// Critical section of code here
	semaphore.up();

POSIX: Portable Operating System Interface(for uniX)
- Interface for application programmers
- Created to bring order to many Unix-derived OS's, so applications are portable

The file system abstraction
- File
	- Named collection of data in a file system
	- POSIX file data: sequence of bytes
	- File metadata: size, modification time, owner, security info, access control
- Directory
	- Folder containing files & directories
	- Hierarchical naming
		- /home/ff/cs162/index.html
	- Links and volumes

C High level file API - Streams: Unformatted sequences of bytes with a position(pointer)
- stdin: Normal source of input
- stdout: Normal source of output
- stderr: Diagnostics and errors

Low level file I/O - The RAW system-call interface
int open (const char * filename, int flags p, mode_t mode])
int creat (const char * filename, mode_t mode)
int close (int filedes)

- Integer return from open() is a file descriptor
- Operations on file descriptors:
	- Open system call created an open file description entry in the system-wide table of open files
	- Open file description object in the kernel represents an instance of an open file
	- User is given an integer instead of a pointer to the file description in the kernel for kernel security reasons.

Low level file API
- Read data from open file using file descriptor: ssize_t read()
	- Reads up to maxsize bytes
	- returns bytes read, 0 => EOF, -1 => error
- Write data to open file using file descriptor: ssize_t write()
	- returns number of bytes written
- Reposition file offset within kernel: off_t lseek()

Low level I/O - Other operations
- Operations specific to terminals, devices, networking, etc...
	- e.g., ioctl
- Duplicating descriptors
	- int dup2(int old, int new);
	- int dup(int old);
- Pipes - channel
	- int pipe(int pipefd[2]);
	- Write to pipefd[1] can be read from pipefd[0]
- File locking
- Memory-mapping files
- Async I/O

### Lecture 5 - IPC, Pipes, and Sockets
Web server network process
- Server: Opens up a network socket to listen to requests coming in
- Server: read() call Kernel
- Kernel: Kernel puts thread thats handling read() call to sleep, because there is no data yet, coming from the network
- Hardware: Request arrive to hardware network interface
- Kernel: Network request is copy into the socket buffer in the kernel
- Kernel: read() call gets waken up and data is sent to server
- Server: Parse the request
- Server: read() call to kernel
- Kernel: Hard drive request for data
- Kernel: Hard drive data copy into buffer in kernel
- Kernel: Data is sent to server
- Server: Server receives data and formats a reply
- Server: write() call to kernel
- Kernel: Kernel copy reply from user buffer to network buffer
- Hardware: Sends reply to destination(internet)

IPC(Interprocess Communication): Allows two processes to communicate and share information
UNIX Pipe: Queue inside kernel memory

Process A --> UNIX Pipe --> Process B
- Memory buffer is finite:
	- If producer(A) tries to write when buffer is full, it blocks(Puts to sleep until there is space available)
	- If consumer(B) tries to read when buffer is empty, it blocks(Put to sleep unitl there is data)

Sockets: Endpoints for communications
- Queues to temporarily hold results
- Another mechanism for IPC
Process <--> Socket <--> Internet <--> Socket <--> Process

### Lecture 6 - Synchronization 1: Concurrency and Mutual Exclusion
Process Control Block(PCB)
- Process state
- Process number
- Program counter
- Registers
- Memory limits
- List of open files

Context switch
- Process 0 is running
- Interrupt or system call is executed
- Process state is saved into PCB 0
- State from PCB 1 is reloaded
- Process 1 now is running

Run a thread
- Load its state(registers, PC, stack pointer) into CPU
- Load environment(virtual memory space, etc.)
- Jump to the PC

Atomic operations: An operation that always run to completion or not at all	

### Lecture 7 - Synchronization 2: Semaphores, Lock Implementation, and Atomic Instructions
```c
Producer-Consumer with a bounded buffer
	|Producer		     Consumer|
	|Producer -->	Buffer -->   Consumer|
	|Producer	  	     Consumer|
	--------------------------------------	
```

- Producers put things into a shared buffer
- Consumers take them out
- Need synchronization to coordinate producer/consumer

- Don't want producer and consumer to have to work in lockstep, so put a fixed-size buffer between them
	- Need to synchronize access to the buffer
	- Producer needs to wait if buffer is full
	- Consumer needs to wait if buffer is empty

- Correctness constraints:
	- Consumer must wait for producer to fill buffers, if none full
	- Producer must wait for consumer to empty buffers, if all full
	- Only one thread can manipulate buffer queue at a time

Solution #3 to "Too much milk" problem:
```c
Thread A
	leave note A;
	while(note B) {
		do nothing;
	}
	if (noMilk) {
		buy milk;
	}
	remove note A;

Thread B
	leave note B;
	while(note A) {
		if (noMilk) {
			buy milk;
		}
	}
	remove note B;
```
	
Cons: A thread is waiting(not sleeping), wasting resources while B thread is buying milk

Solution #4 to "Too much milk" problem:
- Any thread acquires lock("&milk_lock), then goes to buy milk.
- If any other thread sees the lock, they will go to sleep.
* This way no other thread is wasting resources waiting until the other thread buys the milk

```c
acquire(&milk_lock);
if (noMilk) {
	buy milk;
}
release(&milk_lock);
```

### Lecture 13 - Memory 1: Address Translation and Virtual Memory
From program to process
- Preparation of a program for execution involves components at:
	- Compile time(gcc)
	- Link/load time(ld)
	- Execution time

Paging: Physical memory in fixed size chunks
- Solution to fragmentation from segments
- Page table(One per process)
	- Resides in physical memory
	- Contains physical page and permission for each virtual page

### Lecture 14 - Memory 2: Virtual Memory, Caching and TLBs
Virtual Address: [Virtual Page Number | Offset]

```c
Page Table: [Page #0 | V,R]
	    [Page #1 | V,R]
	    [Page #2 | V,R,W]
	
Virtual Address --> Page Table --> Physical Address
```

### Lecture 17 - Demand Paging, General I/O, and Storage Devices
![Overview of I/O](/images/io-overview.png)

Bus: Common set of wires for communication among hardware devices

### Lecture 18 - General I/O, Storage Devices, and Performance
Transferring data to/from controller
- Programmed I/O:
    - Each byte is transferred via processor in/out or load/store
    - CPU waits for I/O operation to complete
- Direct Memory Access(DMA):
    - I/O controller transfers data directly to/from memory
    - CPU is free to do other work

Magnetic Disks
- Seek time: Time to position disk head over track
- Rotational latency: Time for desired sector to rotate under head
- Transfer time: Transfer the block of bits(sector) under head

Solid State Drives(SSD)
- Trapped electrons distinguish between 0 and 1
- No moving parts
- Can only write to empty blocks(erase before write)

Ways of measuring performance - Time(s) and Rates(op/s)
- Latency: Time to complete a task or operation
- Response time: Time to initiate an operation and get its response
- Throughput or Bandwidth: Number of operations completed per unit of time
- Start up or overhead time: Time to start a task or operation

### Lecture 19 - File Systems 1: Performance, Queueing Theory, and File System Design
Little's Law: N(Jobs) = λ(Jobs/s) * L(s)
- N(Jobs): The average number of jobs in the system
- λ(Jobs/s): The average arrival rate of jobs per second
- L(s): The average time a job spends in the system, in seconds
- Applies to any stable system
    - In a stable system: Averge arrival rate = Average departure rate
    - Can be applied to any part of the system(queue, processing stages, etc.)

### Lecture 20 - File Systems 2: File System Design
File system: Layer of OS that transform block interface of disks into files, directories, etc.

Classic OS sitation: Take limited hardware interface and provide a more convenient/useful interface
- Naming: Find file by name
- Organize file names with directories
- Organization: Map files to blocks
- Protection: Enforce access restrictions
- Reliability: Keep files intact despite crashes, hardware failures, etc.

FAT(File Allocation Table): Directories
![FAT directories](/images/fat-dir.png)

### Lecture 21 - File Systems 3: File System, Buffering, Realiability, and Transactions
Hard link: Mapping from a file name to an inode in the directory structure

Soft link, symbolic link, or shortcut: Mapping from a file name to another file name

Buffer cache: Memory used to cache kernel resources, including disk blocks and name translations
- Delayed write: Write to disk only when buffer is full
