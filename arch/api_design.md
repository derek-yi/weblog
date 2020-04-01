## 推荐书目  
- unix编程艺术  
> todo  
- API design for C++
> todo
- API Design Principles
[链接](https://wiki.qt.io/API_Design_Principles)

## 设计原则  
- 命名
拼写准确
动宾结构
定语+名词
不用生僻单词
不发明缩写
符合直觉，望文生义

- 简单
单一功能原则

- 正交
> 功能不重叠  

- 无状态
> 无内部数据，调用者之间不互相影响  

- SOLOD原则
> 来自《敏捷软件开发:原则、模式与实践》

## SOLID原则  
- Single Responsibility Principle (SRP) – 职责单一原则  
> 核心的思想是：一个类，只做一件事，并把这件事做好，其只有一个引起它变化的原因。  
- Open/Closed Principle (OCP) – 开闭原则  
> 模块是可扩展的，而不可修改的。也就是说，对扩展是开放的，而对修改是封闭的。  
- Liskov substitution principle (LSP) – 里氏代换原则 
> 软件工程大师Robert C. Martin把里氏代换原则最终简化为一句话：“Subtypes must be substitutable for their base types”。也就是，子类必须能够替换成它们的基类。即：子类应该可以替换任何基类能够出现的地方，并且经过替换以后，代码还能正常工作。另外，不应该在代码中出现if/else之类对子类类型进行判断的条件。里氏替换原则LSP是使代码符合开闭原则的一个重要保证。  
- Interface Segregation Principle (ISP) – 接口隔离原则  
> 接口隔离原则意思是把功能实现在接口中，而不是类中，使用多个专门的接口比使用单一的总接口要好。   
- Dependency Inversion Principle (DIP) – 依赖倒置原则   
> 高层模块不应该依赖于低层模块的实现，而是依赖于高层抽象。  