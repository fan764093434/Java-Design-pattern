Java的常见集中设计模式学习笔记
==============================
1.工厂模式
----------
	专门负责将大量有共同接口的类实例化。工厂模式可以动态决定将哪一个类实例化，不必事先知道每次要实例化哪一个类。
	工厂模式有以下几种形态：
	(1)简单工厂（Simple Factory）模式，又称静态工厂方法模式（Static Factory Method Pattern）。简单工厂模式是类的
	   创建模式，又叫做静态工厂方法（Static Factory Method）模式。 简单工厂模式是由一个工厂对象决定创建出那一种产品类
	   的实例。其实简单工厂模式就是由一个工厂类可以根据传入的参量决定创建出哪一种产品类的实例。
	   实例：有三种水果，他们的父接口就是fruit
       葡萄 Grape
       草莓 Strawberry
       苹果 Apple
       public class FruitGardener {
           /**
           * 静态工厂方法
           */
           public static Fruit factory(String which) throws BadFruitException { 
               if (which.equalsIgnoreCase("apple")){
                    return new Apple();
               } else if (which.equalsIgnoreCase("strawberry")){
                    return new Strawberry();
               } else if (which.equalsIgnoreCase("grape")){
                    return new Grape();
               } else {
                    throw new BadFruitException("Bad fruit request");
               }
           }
       }
       在使用时，客户端只需调用FruitGardener 的静态方法factory()即可。
       使用缺点：对“开-闭”原则的支持不够，如果有新产品加入到系统中，就需要修复工厂类，将必要的逻辑代码加入到工厂类中。
       ![](https://github.com/fan764093434/MusicProgressButton/blob/master/screenshot/example.gif)
       ![](https://github.com/fan764093434/Java-Design-pattern/blob/master/photo/simple-factory.png)
    (2)工厂方法（Factory Method）模式，又称多态性工厂（Polymorphic Factory）模式或虚拟构造子（Virtual Constructor
       模式；是类的创建模式，它的目的是定义一个创建产品对象的工厂接口，将实际创建工作推迟到子类中，工厂方法模式是简单工厂模
       式的进一步抽象和推广，由于使用了多态性，工厂方法模式保持了简单工厂模式的优点，而且克服了简单工厂模式的缺点。
       在工厂方法模式中，核心的工厂类不在负责所有的产品创建，而是将具体的创创建工作交给子类去做，而核心类则成为一个抽象工厂
       角色，仅负责给出具体子类必须实现的接口，而不用接触那一产品实例化的细节。这种进一步的抽象化结果，使这种工厂方法模式可
       以用来允许系统在不修改具体工厂角色的情况下引进新的产品，这正是工厂方法模式优于简单工厂模式的优势所在。
       ![](https://github.com/fan764093434/Java-Design-pattern/blob/master/photo/factory-method-01.png)
       伪代码示例：
       //创建工厂类
       public interface Creator{
           /*** 工厂方法*/
           public Product factory();
       }
       抽象产品角色Product 类的源代码
       public interface Product{
       }
       具体工厂角色ConcreteCreator1 类的源代码
       public class ConcreteCreator1 implements Creator{
            /*** 工厂方法*/
           public Product factory(){
                return new ConcreteProduct1();
           }
       }
       具体工厂角色ConcreteCreator2 类的源代码
       public class ConcreteCreator2 implements Creator{
           /*** 工厂方法*/
           public Product factory(){
                return new ConcreteProduct2();
           }
       }
       具体产品角色ConcreteProduct1 类的源代码
       public class ConcreteProduct1 implements Product{
       
           public ConcreteProduct1(){
                //TODO do something
           }
           
       }
       具体产品角色ConcreteProduct2 类的源代码
       public class ConcreteProduct2 implements Product{
       
           public ConcreteProduct2(){
                //TODO do something
           }
           
       }
       客户端角色Client 类的源代码
       public class Client{
       
            private static Creator creator1, creator2;
            
            private static Product prod1, prod2;
            
            public static void main(String[] args) {
                creator1 = new ConcreteCreator1();
                prod1 = creator1.factory();
                creator2 = new ConcreteCreator2();
                prod2 = creator2.factory();
            }
       }
       注意：工厂方法模式在农场系统中的实现图
       ![](https://github.com/fan764093434/Java-Design-pattern/blob/master/photo/factory-method-02.png)
    (3)抽象工厂（Abstract Factory）模式，又称工具箱（Kit 或Toolkit）模式。是所有形态的工厂模式中最为抽象和最具一般性
       的一种形态，他是工厂方法模式的进一步推广，简略图如下
       ![](https://github.com/fan764093434/Java-Design-pattern/blob/master/photo/abstract-factory-01.png)
       上图中左边的等级结构代表工厂的等级结构，右边两个等级结构分别代表两个不同产品的等级结构，抽象工厂模式可以向客户端提供
       一个接口，似的客户端在不必指定产品的具体类型下，创建多个产品族中的产品对象，

