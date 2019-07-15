## 3.1 duplicated code 重复的代码  
包括完全重复和部分重复的代码块。  
常见部分重复包括一个或多个符号差异  
  
## 3.2 long method 过长函数  
圈复杂度过高  
大于xxx行  
大量if-else或switch-case处理  
过多职责  
  
## 3.3 large class 过大类  
对于c代码，可以类比为过大的结构体，包含多个数据成员和处理函数  
可以考虑分类后拆分  
  
## 3.4 long parameter list 多长参数列   
使用复杂，性能问题，职责过多  

## 3.5 Divergent change 发散式变化   
因为不同的修改反复修改一个函数  
  
## 3.6 shotgun surgery 霰弹式修改  
特别是新增一个同类项修改多个地方  
Divergent Change 是指一个class 受多种变化的影响  
Shotgun Surgery 则是指一种变化引发多个classe相应修改  
  
## 3.7 Feature Envy 依恋情结  
一个模块需要从另一个模块获取大量的数据  
  
## 3.8 Data clumps 数据泥团  
数据泥团的本质是数据之间有依赖或复制关系  
  
## 3.9 Primitive obsession 基本类型偏执  
应多使用语言lib自带的数据对象  
  
## 3.10 switch statements switch惊悚现身（奇怪的翻译）    
switch-case和大量的if-else增加代码复杂度和维护成本  
  
## 3.11 Parallel Inheritance Hierarchies 平行继承体系    
Parallel Inheritance Hierarchies 其实是Shotgun Surgery 的特殊情况。在这种情况下，每当你为某个class 增加一个 subclass，必须也为另一个 class 相应增加一个subclass。  
C语言也可以参考，扩展功能设计不足，导致无关部分被动修改  
  
## 3.12 lazy class 冗赘类  
应该消失的类，可以合并或改为内联处理  
  
## 3.13 Speculative Generality 夸夸其谈未来性  
如果你的某个 abstract class 其实没有太大作用，请运用Collapse Hierarchy（344）。非必要之delegation（委托）可运用 Inline Class（154）除掉。  
如果函数的某些参数未被用上，可对它实施 Remove Parameter（277）。  
如果函数名称带有多余的抽象意味，应该对它实施Rename Method（273）让它现实一些。  
总结就是，对未来的假设因为其他约束已失去意义。  
  
##  3.14 Temporary Field 临时值域  
特点变量要限定特定的可见范围  
  
## 3.15 Message Chains 消息链  
如果你看到用户向一个对象索求（request）另一个对象，然后再向后者索求另一个对象，然后再索求另一个对象……这就是 Message Chain。   
  
## 3.16 Middle Man 中间转手人  
比如说你问主管是否有时间参加一个会议，他就把这个消息委托给他的记事簿，然后才能回答你。很好，你没必要知道这位主管到底使用传统记事簿或电子记事簿抑或秘书来记录自己的约会。  
  
## 3.17 Inappropriate Intimacy 狎昵关系  
有时你会看到两个 classes 过于亲密，花费太多时间去探究彼此的 private 成分。如果这发生在两个人之间，我们不必做卫道之士；但对于 classes，我们希望它们严守清规。  
  
## 3.18 Alternative Classes with Different Interfaces 异曲同工的类  
如果两个函数做同一件事，却有着不同的签名式（signature），请运用 Rename Method  
  
## 3.19 Incomplete Library Class 不完美的程序库类  
如果你只想修改 library classes 内的一两个函数，可以运用Introduce Foreign Method（162）；  
如果想要添加一大堆额外行为，就得运用Introduce Local Extension（164）。  
  
## 3.20 Data Class 纯数据类  
所谓Data Class是指：它们拥有一些值域（fields），以及用于访问（读写）这些值域的函数，除此之外一无长物。  
  
## 3.21 Refused Bequest 被拒绝的遗赠  
subclasses 应该继承 superclass 的函数和数据。但如果它们不想或不需要继承，又该怎么办呢？  
  
## 3.22 Comments 过多的注释  
what 和 why的问题  
  
  

