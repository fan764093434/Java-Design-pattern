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
    (2)工厂方法（Factory Method）模式，又称多态性工厂（Polymorphic Factory）模式或虚拟构造子（Virtual Constructor模式；
    (3)抽象工厂（Abstract Factory）模式，又称工具箱（Kit 或Toolkit）模式。
	

