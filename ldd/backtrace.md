> https://blog.csdn.net/qq_31710263/article/details/105996293

## 1、内核态 
在想查看的函数中使用dump_stack()函数即可  
如：想查看sa6155_tdm_snd_startup函数被调用的情况，可以在sa6155_tdm_snd_startup函数中加入dump_stack()，编译运行即可看到，类似如下信息。  
    6,19566,192668180,-;Call trace:  
    6,19567,192668200,-; dump_backtrace+0x0/0x1f4  
    6,19568,192668207,-; show_stack+0x20/0x2c  
    6,19569,192668223,-; __dump_stack+0x20/0x28  
    6,19570,192668228,-; dump_stack+0x80/0xbc  
    6,19571,192668246,-; sa6155_tdm_snd_startup+0x6c/0x1c4 [machine_dlkm]  
    6,19572,192668254,-; soc_pcm_open+0x188/0x780  
    6,19573,192668259,-; dpcm_be_dai_startup+0x124/0x2a0  
    6,19574,192668265,-; soc_compr_open_fe+0x148/0x308  
    6,19575,192668273,-; snd_compr_open+0x150/0x204  
    6,19576,192668279,-; snd_open+0x11c/0x14c  
    6,19577,192668285,-; chrdev_open+0xbc/0x1b8  
    6,19578,192668290,-; do_dentry_open+0x144/0x300  
    6,19579,192668295,-; vfs_open+0x58/0x84  
    6,19580,192668301,-; path_openat+0x85c/0x1098  
    6,19581,192668306,-; do_filp_open+0x80/0xfc  
    6,19582,192668310,-; do_sys_open+0x13c/0x24c  
    6,19583,192668315,-; compat_SyS_openat+0x38/0x48  
    6,19584,192668320,-; el0_svc_naked+0x34/0x38  
    

## 2、用户态
函数定义  
```c
#include <execinfo.h>  
int backtrace(void **buffer, int size);  
char **backtrace_symbols(void *const *buffer, int size);  
void backtrace_symbols_fd(void *const *buffer, int size, int fd);  
```

函数说明  
backtrace()函数用来获取程序中当前函数的回溯信息，即一系列的函数调用关系，获取到的信息被放在参数buffer中。buffer是一个数组指针，数组的每个元素保存着每一级被调用函数的返回地址。参数size指定了buffer中可存放的返回地址的数量。如果函数实际的回溯层级数大于size，则buffer中只能存放最近的函数调用关系，所以，想要得到完整的回溯信息，就要确保size参数足够大。  
backtrace()函数的返回值为buffer中的条目数量，这个值不一定等于size，因为如果为得到完整回溯信息而将size设置的足够大，则该函数的返回值为buffer中实际得到的返回地址数量。  
通过backtrace()函数得到buffer之后，backtrace_symbols()可以将其中的返回地址都对应到具体的函数名，参数size为buffer中的条目数。backtrace_symbols()函数可以将每一个返回值都翻译成“函数名+函数内偏移量+函数返回值”，这样就可以更直观的获得函数的调用关系。  
经过翻译后的函数回溯信息放到backtrace_symbols()的返回值中，如果失败则返回NULL。需要注意，返回值本身是在backtrace_symbols()函数内部进行malloc的，所以必须在后续显式地free掉。  
backtrace_symbols_fd()的buffer和size参数和backtrace_symbols()函数相同，只是它翻译后的函数回溯信息不是放到返回值中，而是一行一行的放到文件描述符fd对应的文件中。  
特别注意：编译需要增加-rdynamic选项  
man7.org的说明：https://man7.org/linux/man-pages/man3/backtrace.3.html
  
    
    #include <execinfo.h>
    
    /*在想查看的函数中使用user_dump_stack()函数即可*/
    void user_dump_stack(void)
    {
       int j, nptrs;
    #define SIZE 100
       void *buffer[100];
       char **strings;
    
       nptrs = backtrace(buffer, SIZE);
       printf("backtrace() returned %d addresses\n", nptrs);
    
       /* The call backtrace_symbols_fd(buffer, nptrs, STDOUT_FILENO)
          would produce similar output to the following: */
    
       strings = backtrace_symbols(buffer, nptrs);
       if (strings == NULL) {
       perror("backtrace_symbols");
       exit(EXIT_FAILURE);
       }
    
       for (j = 0; j < nptrs; j++)
       printf("%s\n", strings[j]);
    
       free(strings);
    }

