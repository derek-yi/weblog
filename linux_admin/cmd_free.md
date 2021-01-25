=================================================================================================

derek@ubuntu:~/share/github/xlib$ free -h
              total        used        free      shared  buff/cache   available
Mem:          1.9Gi       763Mi        71Mi        20Mi       1.1Gi       995Mi
Swap:         2.0Gi        81Mi       1.9Gi
=================================================================================================

       total  Total installed memory (MemTotal and SwapTotal in /proc/meminfo)

       used   Used memory (calculated as total - free - buffers - cache)

       free   Unused memory (MemFree and SwapFree in /proc/meminfo)

       shared Memory used (mostly) by tmpfs (Shmem in /proc/meminfo)

       buffers
              Memory used by kernel buffers (Buffers in /proc/meminfo)

       cache  Memory used by the page cache and slabs (Cached and SReclaimable in /proc/meminfo)

       buff/cache
              Sum of buffers and cache

       available
              Estimation of how much memory is available for starting new applications, without swapping. Unlike the data provided  by  the  cache  or  free
              fields,  this  field  takes into account page cache and also that not all reclaimable memory slabs will be reclaimed due to items being in use
              (MemAvailable in /proc/meminfo, available on kernels 3.14, emulated on kernels 2.6.27+, otherwise the same as free)

=================================================================================================
//每10s 执行一次命令，共10次
free -s 10 -c 10 -h

=================================================================================================
