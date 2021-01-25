=================================================================================================
## 查看 pid=1234 的进程的 调度策略
chrt -p 1234
pidof gsd-wwan | xargs chrt -p

## 修改调度策略为 SCHED_FIFO, 并且优先级为10(数值越大优先级越高）
chrt -p -f 10 1641 

## 数值越大优先级越低
derek@ubuntu:~/share/github/xlib$ cat /proc/1641/sched
gsd-wwan (1641, #threads: 4)
-------------------------------------------------------------------
policy                                       :                    1
prio                                         :                   89

## min/max
derek@ubuntu:~/share/github/xlib$ chrt -m
SCHED_OTHER min/max priority    : 0/0
SCHED_FIFO min/max priority     : 1/99
SCHED_RR min/max priority       : 1/99
SCHED_BATCH min/max priority    : 0/0
SCHED_IDLE min/max priority     : 0/0
SCHED_DEADLINE min/max priority : 0/0

=================================================================================================
程序的优先级范围为[0,139]，有效的实时优先级（RT priority）范围为[0,99]，SCHED_NORMAL和SCHED_BATCH这两个非实时任务的优先级为[100,139]。
[100,139]这个区间的优先级又称为静态优先级(static priority)。之所以称为静态优先级是因为它不会随着时间而改变，
内核不会修改它，只能通过系统调用nice去修改。静态优先级用进程描述符中的static_prio表示。

用户的nice值[-20,19]对应于静态优先级的[100,139]，也就是说，nice值越小，优先级越高。
PRI(new)=PRI(old)+nice

然而最后影响CFS调度器调度进程的并不只是优先级的nice值，因为CFS说了，我要让每个进程获得的处理器时间都是一样的（虽然不可能），
所以有一个vruntime的值表示进程运行的虚拟时间（就是在处理器上跑的时间累加和），这个vruntime值越小，说明该进程应该被优先执行（或者获得更多的处理器时间片），因为他饿了。。。
一次调度间隔的虚拟运行时间=实际运行时间*（NICE_0_LOAD/权重）这就是nice值和vruntime之间的关系，其中，NICE_0_LOAD是nice为0时的权重
当nice值为0证明虚拟运行时间=实际运行时间

## Run COMMAND with an adjusted niceness
nice -n 10 vim 

=================================================================================================
