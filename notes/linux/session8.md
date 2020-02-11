## Session 8. File management

Computer applications need to store and retrieve information.
While process is running, PC can store limited info with the process itself.

**_Requirements for Information Storage _**

-   Must be able to store large amount of data
-   Info must survive the termination of the process
-   Multiple processes must be able to access info concurrently
-   Access has to be quick as well

**_File definition and requirements_**

-   Files are logical units of information created by processes
-   Processes can read files and create new ones if needed
-   Info stored files must be persistent(not changing)
-   Files are managed by operating system

OS need to handle different file types like:
`.doc .exe .cpp .ppt .bat .sh .pdf`
where it runs different program to process it on execution request

**_Minimal set of requirements_**

Each user can:

-   manipulate
-   controll access to other user files
-   restructure the user's files in a form appropriate to the problem
-   move data between files
-   back up / recover user's files in case of damage
-   Access by using symbolic names (string names)

In other words, these are the operations to perform on the file:

> Create Delete Open Close Read/write Append Seek Getattributes Setattributes Rename

Seek - for random access fiels, a method is needed to specify from where to take the data
Get attributes - processes often reads attributes to do their work
Set attributes - Some of them set by user AND changable after file is created

**_Files and directories_**

-   Files are stored on disk, where devices store data in blocks
-   Different devices use diff. block size
-   OP need to hiide these device-dependant aspects!
-   File system lets you refer file by a name

-   File System(FS) stores info in **volumes**
    -   usually volume is single device
    -   single devices can be partitioned into >1 volumes
    -   single volume can span multiple devices also ;)
-   Each volume is treated as a numbered sequence of blocks
    -   FS needs to keep track of file names and correcponding block numbers
-   A list of file names and locations is called - **directory**
-   There must be a _root directory_ on each volume

**_Multiple volumes in Unix_**

-   Unix uses a unified FS
-   There is a root FS (initially single volume)
    -   additional volumes are mouted as subdirectories within ROOT!
    -   usually under :root:/mnt folder we mount volumes (ie. /mnt/usb1 ...)

**_File attributes_**

Every file has a description like this:

-   File type (executable, block special etc)
-   Permissions (read, write etc)
-   Owner
-   Group
-   File Size
-   File access, change and modification time
-   File deletion time
-   Number of links (soft/hard)
-   Access Control List (ACLs)
-   Inodes number - ls -i /etc/passwd

Links

It is sometimes useful to keep the same file in several places

> Keep copies. But after changes we need to update both

Links can only refer to files on save volume

> solution: soft links which are files containing the pathname of the file being linked to

![example](https://i.gyazo.com/7e3d39174ce058e2320d3a36b8b33e92.png)

**_Access permisssions_**

-   read, write, execute, delete, append
-   Unix: each user belongs to one or more groups
-   Windows: each file has an access control list

**_FS examples_**

-   FAT (MS-DOS, Windows)
    -   used for floppy disks
-   Ext2fs (Linux second extended filesystem)
    -   extends an original BSD Unix filesystem
-   NTFS (Windows)

**_Ext2fs_**

-   Disk is divided into BLOCK GROUPS
    >     files allocated within a single block group if possible to reduce fragmentation
-   Each block group contains:
    -   superblock (a copy of dist layout information)
    -   block bitmap(0 = free, 1 = in use)
    -   inode bitmap(0 = free, 1 = in use)
    -   inode table
    -   data bblocks (lets say all blocks are 1KB)

![example](https://i.gyazo.com/0d10031a79cf8441be2e0fc31566914a.png)

-   Directory entries contains filename and inode number
    -   inode contains all other file info
-   Inode are 128BYTES (8 can fit per block)
    -   file type (file, dir, link, device), owner, group, permissions, last update. links to data blocks
    -   permissions are rwx for: owner, group, public
-   Inode contains 15 block numbers
    -   1-12 direct link to first 12 blocks of file (so small files are handled well)
    -   single indirect block points to data block containing 256 more block numbers
    -   double indirect block points to data blocks containint 256 more single indirect block numbers
    -   triple indirect block points to data block containining 256 more single indirect block numbers

![example](https://i.gyazo.com/3bd58baeabbb081f9dc43c2a96c262e8.png)
