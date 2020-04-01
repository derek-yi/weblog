## 依赖倒置的场景需求：

1） 模块A、B互相依赖，耦合较大，希望改成单向依赖

2）模块A是底层，模块B是上层，底层不应该调用上层，即只允许B调用A。

 

## 未倒置前，A调用B：
module_a_func  
  调用module_b_func(in_data, out_data)  

module_b:  
  提供module_b_func  

 

## 倒置后，B调用A：

module_a:  
提供func_register(int modid, int (*proc)func(indata_t in, outdata_t out));  
module_a_func:  
  //call register func  

module_b:  
  提供module_b_func  
在模块B或其他初始化注册函数:  
func_register(b, module_b_func）  


## 观察者模式
更进一步，模块C也调用func_register注册一个函数，模块A分别调用B/C注册的函数，这就是所谓的观察者模式了

module_c:  
  提供module_c_func  
在模块C或其他初始化注册函数:  
func_register(c, module_c_func）

