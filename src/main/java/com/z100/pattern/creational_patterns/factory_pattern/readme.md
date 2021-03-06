## 工厂模式



### 简单工厂模式

这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式

- 抽象产品；多个具体产品；一个工厂类；一个client类；
  - 抽象产品：定义了产品的结构，如属性，方法 （如shape）
  - 多个具体产品：具体的产品可能有多个（如circle, rectangle, square...)
  - 一个工厂类负责创建各个具体产品（if else逻辑，如根据参数Type）
  - client类负责创建 工厂类实例，传入不同参数创建不同具体产品
- 违反了开闭原则，工厂类创建产品一般是通过参数判断不同类型，返回不同的具体产品，简单地说就是一些if else的逻辑，如果有新的具体产品，需要在工厂类中添加if else的逻辑，修改了代码，所以说**违反了开闭原则**
- 但是实现简单，适合于具体的产品数量较少的简单场景



### 工厂方法模式

- 一个抽象产品；多个具体产品；一个抽象工厂；多个具体工厂；一个client类
  - 如 shape (circle, rectangle, square...)
  - 如 factory(circleFactory, rectangleFactory, squareFactory...)
  - client类创建各个具体工厂实例，各个工厂实例分别创建自己的产品
- 相比于简单工厂模式，将创建产品的逻辑延迟到各个具体工厂类进行，而非在一个工厂类统一创建多个产品。**遵守了开闭原则**
- 但是存在“类爆炸”的弊端，每次添加一个产品，都需要新增一个具体产品类，以及一个相应的具体工厂类。产品较多时，类的数量较多，在一定程度上增加了系统的复杂度，同时也增加了系统具体类的依赖



### 抽象工厂模式

- 多个抽象产品；多个具体产品；一个抽象工厂，多个具体工厂；一个client类
  - 多个抽象产品，如computer, mouse, pen, screen...
  - 多个具体产品，如(dellComputer, appleComputer...),(dellMouse, appleMouse...),(...),(...)
  - 一个抽象工厂，规定了具体工厂创建逻辑，如createComputer, createMouse...
  - 多个具体工厂，对应各个产品族，每个产品族工厂可以创建多个产品等级的产品
  - 一个client类，创建各个具体工厂实例，每个实例都可以生产多个产品等级产品
- 相比于工厂方法模式只关注一个产品等级（如都关注鼠标这个产品等级），抽象工厂模式更加关注产品族，产品族就是一系列产品的共性，如dell鼠标，dell主机，dell显示器等不同类别的产品都是dell公司的产品
  - 产品等级：一种类型的产品（如dell鼠标，apple鼠标，hp鼠标等）
  - 产品族：多种产品组成的系列（如dell鼠标，dell显示器，dell主机等组成了完整的dell电脑）
- 优点：
  - 解决更加复杂的业务场景
  - 提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类
  - 当一个产品族中的多个对象被设计成一起工作时，它能保证客户端始终只使用同一个产品族中的对象。
- 缺点
  - 产品族扩展非常困难，要增加一个系列的某一产品，既要在抽象的 Creator 里加代码，又要在具体creator的里面加代码。
  - **违反了开闭原则**



### 总结



- 简单工厂模式
  - 简单场景，实现简单；
  - 违反开闭原则
- 工厂方法模式
  - 延迟到具体工厂创建具体产品
  - 遵守开闭原则
  - 存在类爆炸的弊端，增加系统复杂
- 抽象工厂模式
  - 实现相对复杂
  - 违反开闭原则
  - 工厂方法的延续，更加关注产品族，更适用于更加多样复杂的业务场景