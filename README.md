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
    (2)����������Factory Method��ģʽ���ֳƶ�̬�Թ�����Polymorphic Factory��ģʽ�����⹹���ӣ�Virtual Constructorģʽ��
    (3)���󹤳���Abstract Factory��ģʽ���ֳƹ����䣨Kit ��Toolkit��ģʽ��
	

