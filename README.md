Java�ĳ����������ģʽѧϰ�ʼ�
==============================
1.����ģʽ
----------
	ר�Ÿ��𽫴����й�ͬ�ӿڵ���ʵ����������ģʽ���Զ�̬��������һ����ʵ��������������֪��ÿ��Ҫʵ������һ���ࡣ
	����ģʽ�����¼�����̬��
	(1)�򵥹�����Simple Factory��ģʽ���ֳƾ�̬��������ģʽ��Static Factory Method Pattern�����򵥹���ģʽ�����
	   ����ģʽ���ֽ�����̬����������Static Factory Method��ģʽ�� �򵥹���ģʽ����һ���������������������һ�ֲ�Ʒ��
	   ��ʵ������ʵ�򵥹���ģʽ������һ����������Ը��ݴ���Ĳ���������������һ�ֲ�Ʒ���ʵ����
	   ʵ����������ˮ�������ǵĸ��ӿھ���fruit
       ���� Grape
       ��ݮ Strawberry
       ƻ�� Apple
       public class FruitGardener {
           /**
           * ��̬��������
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
       ��ʹ��ʱ���ͻ���ֻ�����FruitGardener �ľ�̬����factory()���ɡ�
       ʹ��ȱ�㣺�ԡ���-�ա�ԭ���֧�ֲ�����������²�Ʒ���뵽ϵͳ�У�����Ҫ�޸������࣬����Ҫ���߼�������뵽�������С�
       ![](https://github.com/fan764093434/Java-Design-pattern/blob/master/photo/simple-factory.png)
    (2)����������Factory Method��ģʽ���ֳƶ�̬�Թ�����Polymorphic Factory��ģʽ�����⹹���ӣ�Virtual Constructor
       ģʽ������Ĵ���ģʽ������Ŀ���Ƕ���һ��������Ʒ����Ĺ����ӿڣ���ʵ�ʴ��������Ƴٵ������У���������ģʽ�Ǽ򵥹���ģ
       ʽ�Ľ�һ��������ƹ㣬����ʹ���˶�̬�ԣ���������ģʽ�����˼򵥹���ģʽ���ŵ㣬���ҿ˷��˼򵥹���ģʽ��ȱ�㡣
       �ڹ�������ģʽ�У����ĵĹ����಻�ڸ������еĲ�Ʒ���������ǽ�����Ĵ�����������������ȥ���������������Ϊһ�����󹤳�
       ��ɫ����������������������ʵ�ֵĽӿڣ������ýӴ���һ��Ʒʵ������ϸ�ڡ����ֽ�һ���ĳ��󻯽����ʹ���ֹ�������ģʽ��
       ����������ϵͳ�ڲ��޸ľ��幤����ɫ������������µĲ�Ʒ�������ǹ�������ģʽ���ڼ򵥹���ģʽ���������ڡ�
       ![](https://github.com/fan764093434/Java-Design-pattern/blob/master/photo/factory-method-01.png)
       α����ʾ����
       //����������
       public interface Creator{
           /*** ��������*/
           public Product factory();
       }
       �����Ʒ��ɫProduct ���Դ����
       public interface Product{
       }
       ���幤����ɫConcreteCreator1 ���Դ����
       public class ConcreteCreator1 implements Creator{
            /*** ��������*/
           public Product factory(){
                return new ConcreteProduct1();
           }
       }
       ���幤����ɫConcreteCreator2 ���Դ����
       public class ConcreteCreator2 implements Creator{
           /*** ��������*/
           public Product factory(){
                return new ConcreteProduct2();
           }
       }
       �����Ʒ��ɫConcreteProduct1 ���Դ����
       public class ConcreteProduct1 implements Product{
       
           public ConcreteProduct1(){
                //TODO do something
           }
           
       }
       �����Ʒ��ɫConcreteProduct2 ���Դ����
       public class ConcreteProduct2 implements Product{
       
           public ConcreteProduct2(){
                //TODO do something
           }
           
       }
       �ͻ��˽�ɫClient ���Դ����
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
       ע�⣺��������ģʽ��ũ��ϵͳ�е�ʵ��ͼ
       ![](https://github.com/fan764093434/Java-Design-pattern/blob/master/photo/factory-method-02.png)
    (3)���󹤳���Abstract Factory��ģʽ���ֳƹ����䣨Kit ��Toolkit��ģʽ����������̬�Ĺ���ģʽ����Ϊ��������һ����
       ��һ����̬�����ǹ�������ģʽ�Ľ�һ���ƹ㣬����ͼ����
       ![](https://github.com/fan764093434/Java-Design-pattern/blob/master/photo/abstract-factory-01.png)
       ��ͼ����ߵĵȼ��ṹ�������ĵȼ��ṹ���ұ������ȼ��ṹ�ֱ����������ͬ��Ʒ�ĵȼ��ṹ�����󹤳�ģʽ������ͻ����ṩ
       һ���ӿڣ��ƵĿͻ����ڲ���ָ����Ʒ�ľ��������£����������Ʒ���еĲ�Ʒ����

