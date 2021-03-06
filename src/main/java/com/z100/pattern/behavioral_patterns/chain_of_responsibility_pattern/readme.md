

### 责任链模式

顾名思义，责任链模式（Chain of Responsibility Pattern）为请求创建了一个接收者对象的链。这种模式给予请求的类型，对请求的发送者和接收者进行解耦。这种类型的设计模式属于**行为型模式**。



在这种模式中，通常每个接收者都包含对另一个接收者的引用。如果一个对象不能处理该请求，那么它会把相同的请求传给下一个接收者，依此类推。



**意图**

避免请求发送者与接收者耦合在一起，让多个对象都有可能接收请求，将这些对象连接成一条链，并且沿着这条链传递请求，接收者处理完请求后将请求传递给链条下一个接受者



**优点**

- 降低请求发送方与请求接收方（也就是请求处理方的耦合度）
  - 请求发送方只需要把请求发送给责任链对象即可，然后请求责任链上的各个结点 根据条件尝试处理逻辑 并传递给责任链上的下一个接收者
- 简化了对象。使得对象不需要知道链的结构
  - 请求发送方只需要把请求发送给责任链对象，不需要知道链的结构。责任链的各个结点也只需要接收由发送方传来的信息或者由上一个结点的传来的信息，并根据逻辑尝试进行处理，然后传递信息给下一个结点

**缺点**

-  不能保证请求一定被接收
- 系统性能将受到一定影响，而且在进行代码调试时不太方便，可能会造成循环调用。
- 可能不容易观察运行时的特征，有碍于除错。