# Simple-File-System
This is a Simple File system made in C. This emulates a single directory disk of 42 MB in a .data file.

The file is named CFS.data which is 42 MB in total. The file is divided into 3 segments namely:

1. Super Block 
    This stores the information about the disk like:
    - the total size.
    - the number of data blocks on disk.
    - the size of one data block.
    - the bit map vector for the disk.
      (an array named "free" representing which data blocks are currently free. free[i] is 0 if the ith data block is empty and free to use otherwise 1.)
    - number of empty data blocks in the file.
    - number of full data blocks in the file.
 
2. Directory
    This stores the metadata about the files present in the file system and also the file table for the file system like:
    - The file table is the array named "files"
      -> isCreated for files[i] is 0 if the index i in the file table is not pointing to any file, otherwise 1.
      -> If isCreated for files[i] is 1 then file name, number of data blocks occupied by file[i] and the list of data blocks occupied by file[i] is              given.
    - The maximum size for a file (in number of data blocks)
    - The maximum number of files allowed in the file system.
  
3. Data Blocks
    This is the area where data for the files is stored. There are in total 1000 data blocks present in the file system each of size 4096 bytes or 4KB.

Constraints of this file system:
  1. The size of the disk (file system) is 42MB.
  2. The file system is single directory only. This means that not directories can be created in the file system.
  3. There are 1000 data blocks available to be used. Each data block has a size of 4096 bytes or 4KB.
  4. The file system allows a maximum of 100 files only.
  5. The file name for a file cannot exceed 100 characters.
  6. The maximum number of data blocks that a file can occupy is 10. So gives the maximum size for a file to be 40KB.
  7. Files in the file system are uniquely identified by file name.
  8. File once made cannot be extended beyonf the initial number of data blocks that it occupies.

Features of this file system:
  1. Linear list (named "files" present in the structure named "directory") is used to find files in the file system.
  2. Linked list allocation method is used to alocate data blocks to a file. This allows for non-contiguous allocation.
  3. Bit vector (array named "free" in the structure named "superBlock") is used for free space management on the disk.
  4. The file sysetm allows for the creation of empty files (files which take up 0 data blocks).

To run the file system:
1. Open terminal in the folder in which the code files are present.
2. type gcc fileSystem.c
3. then run the executable file name a.out.

The first thing the program asks for is if the user wants to foramt the disk or user it as it is. Choosing to format erases all the files previously made and the program goes on to rewerite the superblock and directory freshly.
Otherwise the data remains intact and the user can access the files he/she made in previous sessions.

When editing a file, a user can do it in per block basis, the program goes through all the block the file occupies and asks if the user wants to edit or remove that block or not.
