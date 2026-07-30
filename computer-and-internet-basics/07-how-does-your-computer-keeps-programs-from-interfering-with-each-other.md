# How Does Your Computer Keep Programs from Interfering with Each Other?

You're designing a banner on Figma while your web browser, music player, and chat application are all running. If Figma crashes, the other programs usually keep working. Even a badly behaved program rarely damages another program's data.

That is by careful design. One of the primary jobs of an operating systems is to keep programs separated from one another.

Every running program is a **process**. Every running process behaves as though it owns its own private block of memory. When it stores a variable or loads part of its code, it uses memory addresses that appear to belong only to it.

That private view of memory is called a **virtual address space**.

Of course, the computer doesn't contain separate RAM chips for every program. All processes ultimately share the same physical memory.

The trick is that programs never access physical memory directly.

Every memory address a program uses is translated into a physical address before the processor reads or writes any data. This translation is performed by a piece of hardware called the **Memory Management Unit (MMU)**. The operating system tells the MMU which parts of physical memory belong to each process.

As a result, two different processes can both use the same memory address, yet those addresses can point to completely different places in RAM. Each process sees only its own virtual address space, never another process's.

This translation is what keeps programs from interfering with one another.

If a program tries to read or write memory that doesn't belong to it, the MMU refuses the request and immediately notifies the operating system. The operating system usually stops the program before it can damage another process or the system itself.

On Linux and macOS, this often appears as a **segmentation fault**. On Windows, the same kind of error is usually reported as an **access violation**. Although the names are different, both mean the program tried to access memory it wasn't allowed to use.

Keeping programs separate is only one part of the story.

The operating system also has to make the computer's limited RAM look much larger than it really is. It does this with virtual memory.

Memory is divided into small fixed-size blocks called _pages_. The operating system keeps track of which pages belong to each process and which pages are currently stored in RAM.

If RAM begins to fill up, the operating system can move pages that haven't been used recently from RAM to storage, freeing memory for pages that active programs need right now. If one of those pages is needed again later, the operating system quietly loads it back into RAM.

Most of the time, you never notice this happening. Modern computers have far more RAM than computers did 20 years ago, so users rarely experience heavy paging during normal use. But if the operating system has to move pages between RAM and storage too often, the computer becomes noticeably slower because storage is much slower than RAM.

To understand why, it helps to know that your computer doesn't have just one kind of memory.

Instead, it uses a _memory hierarchy_. Different kinds of memory have different speeds, capacities, and costs. Small amounts of very fast memory sit close to the processor, while larger and slower kinds of memory store much more data.

From fastest to slowest, the memory hierarchy looks like this:

* **Processor registers** hold the values the CPU is using right now.
* **CPU cache** keeps recently used instructions and data close to the processor.
* **RAM** stores the programs and data that are currently in use.
* **Storage** (SSDs, HDDs) keeps your files even when the computer is turned off.

Each level is larger than the one above it, but it also takes longer to access. The processor can read data from its registers in less than a nanosecond. CPU cache takes only a few nanoseconds. Accessing RAM typically takes around 50 to 100 nanoseconds. Reading data from an SSD usually takes around 50 to 200 microseconds, which is roughly 1,000 times slower than RAM.

The processor and the operating system work together to keep the data you use most often in the fastest available memory. This happens automatically, all the way from registers down to storage. Most programs never need to know where their data is physically stored at any given moment.

This works because programs tend to reuse the same instructions and data instead of jumping randomly around memory. Computer scientists call this **locality of reference**. Since recently used data is likely to be used again soon, caches and virtual memory can often predict what should stay in fast memory and what can safely be moved to slower memory.

The result is a system that is both safe and efficient. Every process has its own protected view of memory, even though all processes share the same physical hardware. At the same time, the operating system and the processor cooperate to keep frequently used data as close to the CPU as possible, giving your programs the speed they need while protecting them from one another.

Fetching data that lives somewhere else entirely, on a server across the internet, is a different story with its own delays and its own tricks for hiding them. A later article covers how that works.
