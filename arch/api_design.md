## 推荐书目  
- unix编程艺术(https://www.cnblogs.com/WoodJim/p/6520522.html)  
> 模块原则，使用简洁的接口拼合简单的部件； 
> 清晰原则，清晰胜于技巧； 
> 组合原则，设计时考虑拼接组合； 
> 分离原则，策略同机制分离，接口同引擎分离；  
> 简洁原则，设计要简洁，复杂度能低就低； 
> 吝啬原则，除非别无他法，不要编写庞大的程序； 
> 透明性原则，设计要可见，以便审查和调度；  
> 健壮原则，健壮源于透明和简洁；  
> 表示原则，把知识叠入数据以求逻辑的质朴而健壮；  
> 通俗原则，接口设计避免标新立异；  
> 缄默原则，如果一个程序没什么好说的，就缄默；  
> 经济原则，宁花机器一分，不花程序员一秒；  
> 补救原则，出现异常时，马上退出并给出足够的错误信息；  
> 生成原则，避免手工hack，尽量编写程序去生成程序；  
> 优化原则，雕琢前先要有原型，跑之前先学会走；  
> 多样原则，决不相信不二法门；  
> 扩展原则，设计着眼未来，未来总比预想来得快；    
  
- Google API Design Guide
> [link](https://www.bookstack.cn/read/API-design-guide/API-design-guide-README.md)
  
- API Design Principles(QT)
> [link](https://wiki.qt.io/API_Design_Principles)
  
  
## API设计原则  
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
  
