#设计模式七大原则
##单一职责原则
>对类来说，即一个类应该只负责一项职业，如类A负责两个不同的职责：职责1，职责2.当职业1需求变更而改变A时，可能造成职责2执行错误，所以需要将类A的力度分解为A1，A2<br>	
>注意事项和细节：<br>
>>(1)降低类的复杂度，一个类只负责一项职责<br>
>>(2)提高类的可读性，可维护性<br>
>>(3)降低变更引起的风险<br>
>>(4)通常情况下，我们应当遵守单一职责原则，只有逻辑足够简单，才可以在代码级违反单一职责原则；只有类中的方法足够少，可以在方法级别保持单一职责原则<br>
##接口隔离原则
>客户端不应该依赖它不需要的接口，即一个类对另一个累的依赖应该建立在最小的接口上<br>
##依赖倒转原则
>(1)高层模块不应该依赖底层模块，二者都应该依赖其抽象(抽象类，接口)<br>
>(2)抽象不应该依赖细节，细节应该依赖抽象<br>
>(3)依赖倒转的中心思想是面向接口编程<br>
>(4)依赖倒转原则是给予这样的设计理念：相对于细节的多边性，抽象的东西要稳定的多。以抽象为基础搭建的架构比以细节为基础的架构要稳定的多。在java总，抽象指的是接口或抽象类，细节就是具体的实现类<br>
>(5)使用接口或抽象类的目的是制订好规范，而不涉及任何具体的操作，把展现细节的任务交给他们的实现类去完成<br>
>>依赖关系传递的三种方式<br>
>>>(1)接口方式传递
```java
    public class class01{
        public void fun1(Interface1 interface1){ 
            interface1.run();
        }
    }
```
>>>(2)构造方法传递
```java
    public class class01{
        Interface1 interface1;

        public class01(Interface1 interface1){
            this.interface1 = interface1;
        }
	
        public void fun2(){
            this.interface1.run();
        }
    }
```
>>>(3)setter方式传递

##里氏替换原则
>如果对每个类型为T1对象的o1，都有类型为T2的对象o2，使得T1定义的所有程序P在所有的对象o1都替换成o2时，程序P的行为没有发生变化，那么类型T2是类型T1的子类型。换句话说，所有引用基类的地方必须能透明的使用其子类对象<br>
>在使用继承时，遵循里氏替换原则,在子类中尽量不要重写父类的方法<br>
>里氏替换原则告诉我们，继承实际上让两个类的耦合性增强了，在适当的情况下，可以通过聚合，组合，依赖来解决问题。<br>
	
##开闭原则
>最基础、最重要的设计原则<br>
>一个软件实体如类，模块和函数应该对扩展开放(对提供方)，对修改关闭(对使用方)。用抽象构建框架，用实现扩展细节。<br>
>当软件需要变化时，尽量通过扩展软件实体的行为来实现变化，而不是通过修改已有的代码来实现变化<br>
	
##迪米特法则
>一个对象应该对其他对象保持最少的了解<br>
>类与类关系越密切，耦合度越大<br>
>迪米特法则又叫最少知道原则，即一个类对自己依赖的类知道的越少越好。也就是说，对于被依赖的类不管多么复杂，都尽量将逻辑封装在类的内部。对外除了提供的public方法，不对外泄露任何信息<br>
>还有个更简单的定义：只与直接的朋友通信<br>
>>直接的朋友：每个对象都会与其他对象有耦合关系，只要两个对象之间有耦合关系，这俩对象之间就是朋友关系。依赖，关联，组合，聚合都是耦合。其中，我们称出现成员变量，方法参数，方法返回值中的类为直接的朋友，而出现在局部变量中的类不是直接的朋友。也就是说，陌生的类最好不要以局部变量的形式出现在类的内部<br>
	
##合成复用原则
>原则是尽量使用合成/聚合的方式，而不是使用继承

#单例模式
>饿汉式<br>
>>如果该单例使用过则没问题，没使用则会造成内存浪费<br>

>推荐使用<br>
>>双重锁M<br>
>>静态内部类<br>
>>枚举类方式<br>

>源码<br>
>>饿汉式:java.lang.Runtime<br>

#简单工厂模式
>也叫静态工厂模式<br>
>属于创建型模式，是工厂模式的一种。<br>
>是有一个工厂对象决定创建哪一种产品类的实例。<br>
>定义了一个创建对象的类，由这个类来封装实例化对象的行为<br>
>源码：java.util.Calendar<br>


#工厂方法
>定义了一个创建对象的抽象方法，由子类决定要实例化的类。工厂方法模式将对象的实例化推迟到子类<br>
	
#抽象工厂
>定义了一个interface用于创建相关或有依赖关系的对象簇，而无需指明具体的类<br>
>将工厂抽象称两层，AbsFactory和具体实现的工厂子类。使用时可以根据创建对象类型使用对象的工厂子类。这样将单个的简单工厂类变成了工厂簇，便于代码的维护和扩展<br>
>举例：电脑厂生产鼠标和键盘，dell工厂生产dell鼠标和dell键盘，hp工厂生产hp鼠标和键盘，鼠标和键盘就是产品簇<br>

#原型模式
>继承cloneable接口
```java
class main{
    public static void main(String[] args){
        Sheep sheep = (Sheep)super.clone();
    }
}
```
>源码
>>sping中类型为prototype类型的bean的创建<br>
>>applicationContext.getBean("xxx");<br>

>浅拷贝问题
>>拷贝对象里的属性是一个对象a，a这个对象是没法被拷贝的，拷贝后对象对面的对象属性和拷贝对象的对象属性是同一个<br>
>>对于数据类型是基本数据类型的成员变量，浅拷贝会直接进行值传递，也就是下降该属性值复制一份给新的对象<br>
>>对于数据类型是引用数据类型的变量，比如说成员变量是某个数组、某个类的对象等，那么浅拷贝会进行引用传递，拷贝后的对象和源对象的该成员变量都指向同一个实例，这种情况下，改变其中一个对象的值会影响另一个对象。<br>
```java
class Sheep{
    Sheep friend;
}

class main{
    public static void main(String[] args){
        Sheep sheep;
        sheep sheep2 = sheep.clone();
        sheep2.friend = sheep.friend;   //返回的是true
    }
}
```
>为了解决这个问题需要深度拷贝<br>
>>实现方式1:重写clone方法来实现深度拷贝<br>
>>实现方式2:通过对象序列化实现深度拷贝(推荐)<br>

#建造者模式
>4个角色：
>>product(产品角色):一个具体的产品对象<br>
>>builder(抽象建造者):创建一个Product对象的各个指定的接口/抽象类<br>
>>concreteBuilder(具体建造者):实现接口，构建和装配各个部件<br>
>>director(指挥者):构建一个Builder接口的对象。主要用于创建一个复杂的对象。主要有两个作用，一个是隔离了客户与对象的生产过程，二是负责控制产品对象的生产过程<br>
	
>源码
>>java.lang.StringBuilder<br>
>>其中<br>
>>>AppendAble定义了多个append方法(抽象方法)，即抽象建造者,定义了抽象方法<br>
>>>AbstractStringBuilder 实现了Appendable接口方法，它已经一个建造者，只是不能实例<br>
>>>StringBuilder既充当了指挥者,同时又充当了具体的建造者,建造方法的实现由AbstraStringBuilder完成，而StringBuilder继承了AbstractStringBuilder<br>
	
#适配器模式
>将某个类的接口转换成客户端期望的另一个接口表示，主要目的是兼容性，让原本引接口不匹配不能一起工作的两个类可以协同工作，其别名为包装器(Wrapper)<br>
>属于结构型模式<br>
>主要分3类:类适配器模式、对象适配器模式、接口适配器模式<br>
>用户->A接口->适配器->B接口<br>

#桥接模式
>将实现与抽放放在两个不同的层次中，使两个层次可以独立改变<br>
>是一种结构设计模式<br>
>Bridge模式居于类的最小设计原则，通过使用封装、聚合及继承等行为让不同的类承担不同的职业。他的主要特点是把抽象(Abstraction)与行为实现(Implementation)分离开来，从而可以保持各部分的独立性以及应对他们的功能扩展<br>

#装饰者模式
>io流<br>

#组合模式
>大学-学员-专业<br>
>hashMap<br>

#外观模式
>也叫过程模式，其为子系统中国的一组接口提供一个一致的界面，此模式定义了一个高层接口，这个接口使得这一些列子系统更加容易使用<br>
>外观模式通过定义一个一致的接口，用以屏蔽内部子系统的细节，使得调用端只需要根这个接口发生调用，而无需关心这个子系统的内部细节<br>
>当系统需要进行分层设计时，可以考虑Facade模式<br>
>不要过多使用外观模式，有的时候还是直接调用模块比较好<br>

#享元模式
>享元模式经典应用场景就是池技术，String常亮池、数据库连接池、缓冲池等<br>
>常用于系统底层开发，解决系统性能问题<br>
>Integer源码<br>
>Integer.valueOf(int i)<br>
>先判断值是否在IntegerCache中，如果不在，就创建新的Integer对象，否则就直接从缓存池中返回<br>
>如果i在-128到127之间，是直接用享元模式返回，不在这个范围内，则是用new Integer(i)新建一个对象返回<br>
```java
class main{
    public static void main(String[] args){
	    Integer a = Integer.valueOf(100);
	    Integer b = Integer.valueOf(100);
	    Integer c = Integer.valueOf(200);
	    Integer d = Integer.valueOf(200);
	    a==b; 	//true
	    c==d;	//false        
    }
}
```


#代理模式
>三种 静态代理、动态代理(jdk代理、接口代理)和Cglib代理(可以在内存动态的创建对象，不需要实现接口，属于动态代理的范畴)<br>
>>静态代理<br>
>>>在使用时，需要定义接口或者父类，被代理对象于代理对象一起实现相同的接口或者继承相同的父类<br>

>动态代理<br>
>>代理对象不需要实现接口，但是目标对象需要实现接口，否则不能使用动态代理<br>
>>利用jdk的api，动态在内存中构建代理对象<br>
>>>1)代理类所在包java.lang.reflect.Proxy<br>
>>>2)实现代理只需要使用newProxyInstance方法，该方法需要接收3个参数<br>
>>>完整写法是<br>
>>static Object newProxyInstance(ClassLoader loader,Class<?>[] interfaces,InvocationHandler h)<br>