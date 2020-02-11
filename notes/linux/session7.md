## Session 7. Buffer and Cache

**_Contents_**

-   Final memory issues
-   Cache memory
-   The concept of caching
-   Buffers
-   Buffer management

When programs are running, they are stored in the main memory. Because of the huge differences in speed between different types of memory in the computer, transferring from one type of meory to another can be time consuming:

-   RAM -> Registers
-   Hard disk -> RAM
-   CD/DVD -> Hard disk

| Disk type | Speed                    |
| --------- | ------------------------ |
| Internet  | very slow                |
| CD/DVD    | seek time + acccess time |
| Disk      | 10ms                     |
| RAM       | 50ns                     |
| Register  | 2ns                      |

**_The problem_**

-   Our program is in RAM
-   CPU must execute instruction in our process, which means RAM -> Registers
-   RAM is 25 times slower then registers
-   All processes in RAM no choice

**_The solution_**

-   accessing RAM is expensive in terms of registers
-   Solution - put some quicker memory between RAM and CPU
-   This is cache - faster then RAM and slower then registers
-   The technique we use now is called caching
-   Whenever we read something from RAM, we make copy to cache
-   Then we need to access something on RAM, first check it on cache

![Cache hit](https://i.gyazo.com/6782c3ec9848d8d83f5e11914a559af6.png)

**_Caching_**

-   a cache is limited size, so managing the content in there is important
-   cache is only useful if a hit occurs
-   consider 3 types of misses
    -   compulsory misses (first time reference)
    -   capacity misses (when cache is full)
    -   conflict misses (data that was evicted from cache is now needed)

![cache structure](https://i.gyazo.com/fcf53458ec3eb5e9ad73744d4a8471b7.png)

**_Locality_**

-   How low cache size compare to large RAM memory size?
-   The concept of locality
-   Locality helped to speed up RAM access hold blocks of the most recently referenced instructions and data items

1. TEMPORAL LOCALITY: memory that is referenced once is likely to be **referenced multiple times** soon
1. SPATIAL LOCALITY: the program is likely to reference a nearby memory locations in the near future (ie. looping the array)

**_Writing to cache_**

-   Write-through - every write to cache causes a write to data store
    -   more secure if system crashes
    -   have to wait for this to happen
-   Write-back - write to data store is postponed until item is evicted from cache
    -   only last update written to main store
    -   writing is much QUICKER!

**_Cache caherence_**

-   The same piece of data could be stored in several places at the same time
-   Presents a problem in a multi-process environment – what happens if a process shares data with another?

**_Caching as a concept_**

-   The concept of caching can be seen at many levels in the computer, not just main memory
-   Think of a web-cache for your browser – same concept
-   There is also a cache for pages being read from disk to main memory – the page cache – where those process pages and data pages will be stored

**_Buffering_**

> A buffer is an area of memory which is used to store data while it is being transferred to another place

For instance, consider transferring a file via a modem to the hard disk
The file is received via the modem byte by byte and placed into a buffer in main memory
When the buffer is full, the data can be written to memory
While the data is being written to memory, another buffer may be used to keep receiving the file

**_Buffer cache_**

Although caching and buffering are distinct functions, the same region of memory can be used for both
For example, the OS uses buffers in main memory to hold disk data
These buffers are also used as a cache for file I/O to improve efficiency for files
We call this the BUFFER CACHE

The disk driver copies data from and back to the disk, The buffer cache manages these temporary copies of the disk blocks
Keeping frequently-accessed disk blocks in memory reduces the number of disk accesses and makes the system faster
