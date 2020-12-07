# File_Recovery
This is a program written in C++ designed for a Linux system that recovers any file type from a NTFS filesystem to a new partition.

1. Our initial partition has several files and directories.

     Our program lists each file and directory in the partition as a table:

     row of the table is each file and directory - deleted or undeleted.

     columns - a.  Name of the file,  b. Cluster run of the file,   c. print TRUE if file active or FALSE if file deleted.

     We did this by reading one cluster at a time starting at MFT.  Each cluster has 4 entries. We called a series of functions to get the file name and cluster run for each of        the entries as well as the delete/active flag.

2. We then deleted a file.  If you list the files again, this time the row for that file will show FALSE - deleted.

3. Our program then recovers it, following these steps: 

      We opened a new file for write operation on a different partition (the name of the file is the file being recovered)  

      Then we read one cluster at a time (from the cluster run) into a buffer. We then wrote this buffer (one cluster at a time) to the file we opened to write


To run:

1. Navigate to linux directory
2. make ntfs

Listing files and if they are deleted or not:

3. sudo ./ntfs/exe/ntfs /dev/sdx# (this is the device that you want to see the files on)

File recovery:

3. sudo ./ntfs/exe/ntfs /dev/sdx# filename.ext /path/to/new/partition/filename.ext
