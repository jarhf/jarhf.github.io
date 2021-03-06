# Determining which parts of a file have changed
  The rsync utility uses an algorithm invented by Australian computer programmer Andrew Tridgell for efficiently transmitting a structure  
(such as a file) across a communications link when the receiving computer already has a similar, but not identical, version of the same  
structure.  
  The recipient splits its copy of the file into chunks and computes two checksums for each chunk: the MD5 hash, and a weaker but easier  
to compute 'rolling checksum'.[18] It sends these checksums to the sender.  
  The sender quickly computes the rolling checksum for each chunk in its version of the file; if they differ, it must be sent. If they're  
the same, the sender uses the more computationally expensive MD5 hash to verify the chunks are the same.  
  The sender then sends the recipient those parts of its file that did not match, along with information on where to merge these blocks  
into the recipient's version. This makes the copies identical. There is a small probability that differences between chunks in the   
sender and recipient are not detected, and thus remain uncorrected. With 128 bits from MD5 plus 32 bits from the rolling checksum,  
the probability is on the order of 2−(128+32) = 2−160.
  The rolling checksum used in rsync is based on Mark Adler's adler-32 checksum, which is used in zlib, and is itself based on Fletcher's  
checksum.
  If the sender's and recipient's versions of the file have many sections in common, the utility needs to transfer relatively little data  
to synchronize the files. If typical data compression algorithms are used, files that are similar when uncompressed may be very different  
when compressed, and thus the entire file will need to be transferred. Some compression programs, such as gzip, provide a special  
"rsyncable" mode which allows these files to be efficiently rsynced, by ensuring that local changes in the uncompressed file yield only  
local changes in the compressed file.
  Rsync supports other key features that aid significantly in data transfers or backup. They include compression and decompression of  
data block by block using zlib, and support for protocols such as ssh and stunnel.

>[https://en.wikipedia.org/wiki/Rsync](https://en.wikipedia.org/wiki/Rsync)
