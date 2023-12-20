
......CSCI 402: Operating Systems ......

///THE CODE FOR THIS PROJECT HAS BEEN REMOVED DUE TO USC POLICY. THE SEGMENTED PRISTINE CODE HAS ONLY BEEN PROVIDED FOR LEARNING PURPOSES AND WILL NOT RUN///

This was a semester-long project created by a series of kernel programming assignments to develop various components of a real operating system (Weenix). It was designed to provide students with hands-on experience in understanding the internals of operating systems. Debugging was addressed using GDB commands to resolve code that has crashed or frozen. Breakpoints were set in lines preceeding these issues, code was stepped through, and then values were printed for potential variables or values causing these issues. Grep command-line searching was also utilized to explore the provided code since this project relied on many given parts while also ommitting other functionalities. Specifically, this project required the creation of processes, drivers, a virtual file system, a system 5 file system, and virtual memory.


Process Management (Phase 1) --------------------------

This phase implements a single-threaded process, guiding the process through the lifecycle of creation, waiting, and destruction. It was necessary to ensure that when a thread gave up the CPU, all global variables and data structures had to be in a consistent state. A thread scheduler was used to transition threads between different states while broadcasting/waking threads waiting in mutex queues to achieve synchronization. Kshell commands were used to invoke test functions via child processes to satisfy KASSERT macros.


File Systems (Phase 2) --------------------------------

The virtual file system implemented was intended to work with any actual file system via polymorphism. To maintain objects, reference counting was used to increment/decrement the references. Once a reference count reached zero, nothing in the system was aware of the object, so these objects were then deleted and freed from memory. This VFS served as the common interface between the operating system kernel and various file systems (S5FS and device drivers). Directories and files were verified through pathname resolution functions and were granted file permissions, making the file system structure more manageable.


Virtual Memory (Phase 3) ------------------------------

The S5FS was based on the original Unix file system via a real disk versus the ramfs previously that did not use a real disk. Virtual memory was used for user address space management at the user level to service system calls. This portion focused on implementing virtual memory maps, page faults, shadow objects, and anonymous objects. The objective was to load the program into memory, build/manipulate the address space, handle page faults, and run system calls. Pages were used to identify objects and their page numbers to allocate/manage/clean memory.