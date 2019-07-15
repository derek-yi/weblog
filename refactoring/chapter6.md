## 6.1 Extract Method  
1) 无参数  
2）带参数  
  
## 6.2 Inline Method  
一个函数，其本体（method body）应该与其名称（method name）同样清楚易懂。  
和6.1相反，如果本体清晰易懂，可以inline到调动地方，删除函数  
  
## 6.3 Inline Temp  
删除只被一次赋值一次使用的变量  
   
## 6.4 Replace Temp with Query  
表达式提炼为独立的函数  
虽有性能损失，但可隐藏数据  
  
## 6.5 Introduce Explaining Variable  
将表达式赋值给变量，增加可读性  
  
## 6.6 Split Temporary Variable  
一个变量不同用途的赋值，说明需要拆分  
  
## 6.7 Remove Assignments to Parameters  
不要把函数参数用作局部变量  
  
## 6.8 Replace Method with Method Object  
？？  
  
## 6.9 Substitute Algorithm  
替换算法（处理逻辑）  
  
