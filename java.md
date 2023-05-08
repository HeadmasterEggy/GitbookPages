# Java

## 封装 <a href="#bzmx6" id="bzmx6"></a>

封装从字面上来理解就是包装的意思，专业点就是信息隐藏，是指利用抽象数据类型将数据和基于数据的操作封装在一起，使其构成一个不可分割的独立实体，数据被保护在抽象数据类型的内部，尽可能地隐藏内部的细节，只保留一些对外接口使之与外部发生联系。系统的其他对象只能通过包裹在数据外面的已经授权的操作来与这个封装的对象进行交流和交互。也就是说用户是无需知道对象内部的细节，但可以通过该对象对外的提供的接口来访问该对象。

对于封装而言，一个对象它所封装的是自己的属性和方法，所以它是不需要依赖其他对象就可以完成自己的操作。使用封装有四大好处：

* 良好的封装能够减少耦合。
* 类内部的结构可以自由修改。
* 可以对成员进行更精确的控制。
* 隐藏信息，实现细节。

封装把一个对象的属性私有化，同时提供一些可以被外界访问的属性的方法，如果不想被外界方法，我们大可不必提供方法给外界访问。但是如果一个类没有提供给外界访问的方法，那么这个类也没有什么意义了。

以下 Person 类封装 name、gender、age 等属性，外界只能通过 get() 方法获取一个 Person 对象的 name 属性和 gender 属性，而无法获取 age 属性，但是 age 属性可以供 work() 方法使用。

注意到 gender 属性使用 int 数据类型进行存储，封装使得用户注意不到这种实现细节。并且在需要修改 gender 属性使用的数据类型时，也可以在不影响客户端代码的情况下进行。

```
public class Person {

    private String name;
    private int gender;
    private int age;

    public String getName() {
        return name;
    }

    public String getGender() {
        return gender == 0 ? "man" : "woman";
    }

    public void work() {
        if (18 <= age && age <= 50) {
            System.out.println(name + " is working very hard!");
        } else {
            System.out.println(name + " can't work any more!");
        }
    }
}
```

## 继承 <a href="#nxuke" id="nxuke"></a>

继承是使用已存在的类的定义作为基础建立新类的技术，新类的定义可以增加新的数据或新的功能，也可以用父类的功能，但不能选择性地继承父类。通过使用继承我们能够非常方便地复用以前的代码，能够大大的提高开发的效率。

继承所描述的是“IS-A”的关系，如果有两个对象 A 和 B ，若可以描述为“A是B”，则可以表示 A 继承 B ，其中B是被继承者称之为父类或者超类， A 是继承者称之为子类或者派生类。

实际上继承者是被继承者的特殊化，它除了拥有被继承者的特性外，还拥有自己独有得特性。例如猫有抓老鼠、爬树等其他动物没有的特性。同时在继承关系中，继承者完全可以替换被继承者，反之则不可以，例如我们可以说猫是动物，但不能说动物是猫就是这个道理，其实对于这个我们将其称之为“向上转型”。

诚然，继承定义了类如何相互关联，共享特性。对于若干个相同或者相识的类，我们可以抽象出他们共有的行为或者属相并将其定义成一个父类或者超类，然后用这些类继承该父类，他们不仅可以拥有父类的属性、方法还可以定义自己独有的属性或者方法。

同时在使用继承时需要记住三句话：

* 子类拥有父类非 private 的属性和方法。
* 子类可以拥有自己属性和方法，即子类可以对父类进行扩展。
* 子类可以用自己的方式实现父类的方法。

在下面这个示例中，我们定义了两个静态内部类：Animal和Dog。Animal类中有一个方法eat()，用于输出“动物吃食物”的字符串。Dog类继承了Animal类，并新增了一个方法bark()，用于输出“狗叫：汪汪汪”的字符串。

```
public class Main {
    public static class Animal {
        public void eat() {
            System.out.println("动物吃食物");
        }
    }

    public static class Dog extends Animal {
        public void bark() {
            System.out.println("狗叫：汪汪汪");
        }
    }

    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat(); // 调用继承自父类Animal的方法
        dog.bark(); // 调用子类Dog的方法
    }
}
```

### &#x20;<a href="#itcuy" id="itcuy"></a>

### 构造器 <a href="#nllgh" id="nllgh"></a>

通过前面我们知道子类可以继承父类的属性和方法，除了那些 private 的外还有一样是子类继承不了的---构造器。对于构造器而言，它只能够被调用，而不能被继承。 调用父类的构造方法我们使用 super() 即可。

构建过程是从父类“向外”扩散的，也就是从父类开始向子类一级一级地完成构建。而且我们并没有显示的引用父类的构造器，这就是 java 的聪明之处：编译器会默认给子类调用父类的构造器。

但是，这个默认调用父类的构造器是有前提的：父类有默认构造器。如果父类没有默认构造器，我们就要必须显示的使用 super() 来调用父类构造器，否则编译器会报错：无法找到符合父类形式的构造器。

对于子类而已,其构造器的正确初始化是非常重要的,而且当且仅当只有一个方法可以保证这点：在构造器中调用父类构造器来完成初始化，而父类构造器具有执行父类初始化所需要的所有知识和能力。

对于继承而言，子类会默认调用父类的构造器，但是如果没有默认的父类构造器，子类必须要显示的指定父类的构造器，而且必须是在子类构造器中做的第一件事(第一行代码)。

### **super关键字调用父类构造方法** <a href="#ommzn" id="ommzn"></a>

在Java中，每个类都有一个构造方法，用于创建这个类的对象。构造方法的主要作用是初始化对象的属性，确保对象能够正常工作。在创建对象时，构造方法会被自动调用。\
\


在继承关系中，子类会自动继承父类的构造方法，但是构造方法不能被继承，只能被调用。因此，在子类中必须显式调用父类的构造方法，以确保父类的属性也能被正确地初始化。这时我们可以使用super关键字来调用父类的构造方法。

使用super关键字调用父类构造方法的格式如下所示：\
`super(参数列表);`

这里的参数列表指的是父类构造方法的参数列表，包括类型和参数名。父类构造方法会根据传入的参数初始化其属性。

#### **示例代码及其分析** <a href="#ovkg5" id="ovkg5"></a>

现在我们来看下面这个示例代码：\
\


```
public class Main {
    public static class Parent {
        private final int age;

        public Parent(int age) {
            this.age = age;
        }

        public int getAge() {
            return age;
        }
    }

    public static class Child extends Parent {
        private final String name;

        public Child(int age, String name) {
            super(age);
            this.name = name;
        }

        public String getName() {
            return name;
        }
    }

    public static void main(String[] args) {
        Child child = new Child(10, "Tom");
        System.out.println("child's age: " + child.getAge()); // 输出：child's age: 10
        System.out.println("child's name: " + child.getName()); // 输出：child's name: Tom
    }
}
```

在Parent类中定义了一个私有属性age，并提供了一个有参构造方法Parent(int age)用于初始化这个属性。在Child类中，我们继承了Parent类，并定义了一个私有属性name，以及一个有参构造方法Child(int age, String name)用于初始化age和name属性。在Child的构造方法中，我们调用了父类Parent的构造方法super(age)，将传入构造方法的age参数传递给父类，以初始化父类的属性。然后再初始化子类Child的属性name。

在Main类的main方法中，我们创建了一个Child对象child，并分别调用了child的getAge方法和getName方法，输出了它的属性值。最终输出结果为：child's age: 10和child's name: Tom。

通过这个例子，我们可以看到，通过使用super关键字，子类Child能够调用父类Parent的构造方法，来初始化父类的属性。这样，我们就能够实现在子类中初始化多重属性，同时也确保了父类中的属性也能被正确地初始化。

### protected关键字 <a href="#tpbyu" id="tpbyu"></a>

private 访问修饰符，对于封装而言，是最好的选择，但这个只是基于理想的世界，有时候我们需要这样的需求：我们需要将某些事物尽可能地对这个世界隐藏，但是仍然允许子类的成员来访问它们。这个时候就需要使用到 protected。

对于 protected 而言，它指明就类用户而言，他是 private，但是对于任何继承与此类的子类而言或者其他任何位于同一个包的类而言，他却是可以访问的。

#### 示例代码及其分析 <a href="#xtoxp" id="xtoxp"></a>

```
// Vehicle.java
class Vehicle {
    private int speed;

    protected void run() {
        System.out.println("Vehicle is running at " + getSpeed() + " km/h");
    }

    protected void setSpeed(int speed){
        this.speed = speed;
    }

    protected int getSpeed(){
        return speed;
    }
}

// Car.java
class Car extends Vehicle {
    public Car(int speed) {
        setSpeed(speed);
    }
}

// Main.java
public class Main {
    public static void main(String[] args) {
        Car car = new Car(120);
        car.run(); // 输出：Vehicle is running at 120 km/h
    }
}
```

#### 关于作用： <a href="#w7xm2" id="w7xm2"></a>

* protected访问修饰符允许其子类访问其定义的成员（方法和变量），并且允许同一个包内的其他类访问这些成员；
* private访问修饰符用来限定某个成员只能在定义该成员的类内部被访问。

在这个例子中，将run()方法和speed成员变量定义为protected和private访问修饰符，可以确保speed成员变量只有在Vehicle类及其子类（例如Car类）中被访问和修改，保证了程序的安全性。

### 向上转型 <a href="#qtjee" id="qtjee"></a>

在上面的继承中我们谈到继承是 IS-A 的相互关系，猫继承与动物，所以我们可以说猫是动物，或者说猫是动物的一种。这样将猫看做动物就是向上转型。

Cat 可以当做 Animal 来使用，也就是说可以使用 Animal 引用 Cat 对象。父类引用指向子类对象称为**向上转型**。

```
Animal animal = new Cat();
```

向上转型是指将一个子类对象赋值给一个父类引用变量的过程，可以将子类对象当做父类对象对待。这个过程可以自动完成，因为子类对象包含了父类对象的全部特性，所以它可以被当作父类对象使用。在向上转型中，虽然父类引用变量只能看到从父类继承而来的属性和方法，但是实际执行的方法却是子类的方法，并且还能够访问子类中扩展的属性和方法。以下是一个例子：

```
class Animal {
    public void move() {
        System.out.println("Animal is moving!");
    }
}

class Cat extends Animal {
    @Override
    public void move() {
        System.out.println("Cat is moving!");
    }

    public void jump() {
        System.out.println("Cat is jumping!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Cat();  // 向上转型
        animal.move();  // 执行的是 Cat 类中的 move() 方法
        //animal.jump();  // 编译错误，Animal 类型没有 jump() 方法

        Cat cat = new Cat();
        cat.move();  // 执行的是 Cat 类中的 move() 方法
        cat.jump();  // 执行 Cat 类中的 jump() 方法
    }
}
```

在上面的例子中，Cat 类继承自 Animal 类，并覆盖了 Animal 类中的 move() 方法，同时还新增了 jump() 方法。在 main() 方法中，Animal 类型的引用变量 animal 指向了 Cat 类型的对象，这就是向上转型，此时调用 move() 方法实际执行的是 Cat 类中的 move() 方法，因为 Cat 类覆盖了父类的 move() 方法。但是如果尝试调用 jump() 方法，就会导致编译错误，因为 jump() 方法是子类新增的方法，而 Animal 类没有实现该方法。在这个例子中，我们展示了向上转型的用法，即将子类对象当做父类对象对待，以实现代码的灵活使用和复用。

在向上转型的过程中，父类引用变量只能看到从父类继承而来的属性和方法，而子类中新增的方法和属性是无法被父类引用变量访问的。但是，如果子类覆盖了从父类继承而来的方法，并且在子类中重新实现了该方法，那么在父类引用变量调用该方法的时候，实际执行的是子类中重新实现的方法。这个过程中并没有修改父类的方法，而是在子类中重新实现了该方法，称为方法的覆盖。

### 谨慎继承 <a href="#iwgi5" id="iwgi5"></a>

在这里我们需要明确，继承存在如下缺陷：

* 父类变，子类就必须变。
* 继承破坏了封装，对于父类而言，它的实现细节对与子类来说都是透明的。
* 继承是一种强耦合关系。

所以说当我们使用继承的时候，我们需要确信使用继承确实是有效可行的办法。那么到底要不要使用继承呢？**《Think in java》** 中提供了解决办法：问一问自己是否需要从子类向父类进行向上转型。如果必须向上转型，则继承是必要的，但是如果不需要，则应当好好考虑自己是否需要继承。

## 多态 <a href="#ilygk" id="ilygk"></a>

所谓多态就是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量倒底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。因为在程序运行时才确定具体的类，这样，不用修改源程序代码，就可以让引用变量绑定到各种不同的类实现上，从而导致该引用调用的具体方法随之改变，即不修改程序代码就可以改变程序运行时所绑定的具体代码，让程序可以选择多个运行状态，这就是多态性。

多态分为**编译时多态**和**运行时多态**:

* 编译时多态主要指**方法的重载**
* 运行时多态指**程序中定义的对象引用所指向的具体类型在运行期间才确定**

所以对于多态我们可以总结如下：

指向子类的父类引用由于向上转型了，它只能访问父类中拥有的方法和属性，而对于子类中存在而父类中不存在的方法，该引用是不能使用的，尽管是重载该方法。若子类重写了父类中的某些方法，在调用该些方法的时候，必定是使用子类中定义的这些方法（动态连接、动态调用）。

对于面向对象而言，多态分为编译时多态和运行时多态。其中编辑时多态是静态的，主要是指方法的重载，它是根据参数列表的不同来区分不同的函数，通过编辑之后会变成两个不同的函数，在运行时谈不上多态。而运行时多态是动态的，它是通过动态绑定来实现的，也就是我们所说的多态性。

### 多态的实现条件 <a href="#gzpxu" id="gzpxu"></a>

在刚刚开始就提到了继承在为多态的实现做了准备。子类 Child 继承父类 Father，我们可以编写一个指向子类的父类类型引用，该引用既可以处理父类 Father 对象，也可以处理子类 Child 对象，当相同的消息发送给子类或者父类对象时，该对象就会根据自己所属的引用而执行不同的行为，这就是多态。即多态性就是相同的消息使得不同的类做出不同的响应。

Java实现多态有三个必要条件：**继承**、**重写**、**向上转型**。

* **继承**：在多态中必须存在有继承关系的子类和父类。
* **重写**：子类对父类中某些方法进行重新定义，在调用这些方法时就会调用子类的方法。
* **向上转型**：在多态中需要将子类的引用赋给父类对象，只有这样该引用才能够具备技能调用父类的方法和子类的方法。

只有满足了上述三个条件，我们才能够在同一个继承结构中使用统一的逻辑实现代码处理不同的对象，从而达到执行不同的行为。

对于Java而言，它多态的实现机制遵循一个原则：当超类对象引用变量引用子类对象时，被引用对象的类型而不是引用变量的类型决定了调用谁的成员方法，但是这个被调用的方法必须是在超类中定义过的，也就是说被子类覆盖的方法。

下面的代码中，乐器类 (Instrument) 有两个子类: Wind 和 Percussion，它们都覆盖了父类的 play() 方法，并且在 main() 方法中使用父类 Instrument 来引用 Wind 和 Percussion 对象。在 Instrument 引用调用 play() 方法时，会执行实际引用对象所在类的 play() 方法，而不是 Instrument 类的方法。

```
public class Instrument {
    public void play() {
        System.out.println("Instrument is playing...");
    }
}

public class Wind extends Instrument {
    public void play() {
        System.out.println("Wind is playing...");
    }
}

public class Percussion extends Instrument {
    public void play() {
        System.out.println("Percussion is playing...");
    }
}

public class Music {
    public static void main(String[] args) {
        List<Instrument> instruments = new ArrayList<>();
        instruments.add(new Wind());
        instruments.add(new Percussion());
        for(Instrument instrument : instruments) {
            instrument.play();
        }
    }
}
```

## 参考资料 <a href="#e1bvs" id="e1bvs"></a>

[https://blog.csdn.net/jianyuerensheng/article/details/51602015](https://blog.csdn.net/jianyuerensheng/article/details/51602015)

[https://www.pdai.tech/md/java/basic/java-basic-oop.html](https://www.pdai.tech/md/java/basic/java-basic-oop.html)

## Java 重写与重载 <a href="#tge2l" id="tge2l"></a>

### 重写(Override) <a href="#aiyj6" id="aiyj6"></a>

重写是子类对父类的允许访问的方法的实现过程进行重新编写, 返回值和形参都不能改变。**即外壳不变，核心重写！**

重写的好处在于子类可以根据需要，定义特定于自己的行为。 也就是说子类能够根据需要实现父类的方法。

重写方法不能抛出新的检查异常或者比被重写方法申明更加宽泛的异常。例如： 父类的一个方法申明了一个检查异常 IOException，但是在重写这个方法的时候不能抛出 Exception 异常，因为 Exception 是 IOException 的父类，只能抛出 IOException 的子类异常。

在面向对象原则里，重写意味着可以重写任何现有方法。实例如下：

```
class Animal{
    public void move(){
        System.out.println("动物可以移动");
    }
}
 
classDog extends Animal{
   public void move(){
      System.out.println("狗可以跑和走");
   }
}
 
public class TestDog{
   public static void main(String args[]){
      Animal a = newAnimal(); // Animal 对象
      Animal b = newDog(); // Dog 对象
 
      a.move();// 执行 Animal 类的方法
 
      b.move();//执行 Dog 类的方法
   }
}
```

以上实例编译运行结果如下：

| <p>1</p><p>2</p> | 动物可以移动 |
| ---------------- | ------ |

狗可以跑和走

在上面的例子中可以看到，尽管b属于Animal类型，但是它运行的是Dog类的move方法。

这是由于在编译阶段，只是检查参数的引用类型。

然而在运行时，Java虚拟机(JVM)指定对象的类型并且运行该对象的方法。

因此在上面的例子中，之所以能编译成功，是因为Animal类中存在move方法，然而运行时，运行的是特定对象的方法。

思考以下例子：

```
classAnimal{
   publicvoidmove(){
      System.out.println("动物可以移动");
   }
}
 
classDog extendsAnimal{
   publicvoidmove(){
      System.out.println("狗可以跑和走");
   }
   publicvoidbark(){
      System.out.println("狗可以吠叫");
   }
}
 
publicclassTestDog{
   publicstaticvoidmain(String args[]){
      Animal a = newAnimal(); // Animal 对象
      Animal b = newDog(); // Dog 对象
 
      a.move();// 执行 Animal 类的方法
      b.move();//执行 Dog 类的方法
      b.bark();
   }
}
```

以上实例编译运行结果如下：

```
TestDog.java:30: cannot find symbol
symbol  : method bark()
location: classAnimal
                b.bark();
                 ^
```

该程序将抛出一个编译错误，因为b的引用类型Animal没有bark方法。

### 方法的重写规则 <a href="#hh9he" id="hh9he"></a>

* 参数列表必须完全与被重写方法的相同。
* 返回类型与被重写方法的返回类型可以不相同，但是必须是父类返回值的派生类（java5 及更早版本返回类型要一样，java7 及更高版本可以不同）。
* 访问权限不能比父类中被重写的方法的访问权限更低。例如：如果父类的一个方法被声明为 public，那么在子类中重写该方法就不能声明为 protected。
* 父类的成员方法只能被它的子类重写。
* 声明为 final 的方法不能被重写。
* 声明为 static 的方法不能被重写，但是能够被再次声明。
* 子类和父类在同一个包中，那么子类可以重写父类所有方法，除了声明为 private 和 final 的方法。
* 子类和父类不在同一个包中，那么子类只能够重写父类的声明为 public 和 protected 的非 final 方法。
* 重写的方法能够抛出任何非强制异常，无论被重写的方法是否抛出异常。但是，重写的方法不能抛出新的强制性异常，或者比被重写方法声明的更广泛的强制性异常，反之则可以。
* 构造方法不能被重写。
* 如果不能继承一个方法，则不能重写这个方法。

### 重载(Overload) <a href="#kxglz" id="kxglz"></a>

重载(overloading) 是在一个类里面，方法名字相同，而参数不同。返回类型可以相同也可以不同。

每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。

最常用的地方就是构造器的重载。

**重载规则:**

* 被重载的方法必须改变参数列表(参数个数或类型不一样)；
* 被重载的方法可以改变返回类型；
* 被重载的方法可以改变访问修饰符；
* 被重载的方法可以声明新的或更广的检查异常；
* 方法能够在同一个类中或者在一个子类中被重载。
* 无法以返回值类型作为重载函数的区分标准。

#### 实例 <a href="#scfx9" id="scfx9"></a>

```
public class Overloading {
    publicinttest(){
        System.out.println("test1");
        return1;
    }
 
    publicvoidtest(inta){
        System.out.println("test2");
    }  
 
    //以下两个参数类型顺序不同
    publicString test(inta,String s){
        System.out.println("test3");
        return"returntest3";
    }  
 
    publicString test(String s,inta){
        System.out.println("test4");
        return"returntest4";
    }  
 
    publicstaticvoidmain(String[] args){
        Overloading o = newOverloading();
        System.out.println(o.test());
        o.test(1);
        System.out.println(o.test(1,"test3"));
        System.out.println(o.test("test4",1));
    }
}
```

### 重写与重载之间的区别 <a href="#abfja" id="abfja"></a>

| **区别点** | **重载方法** | **重写方法**                |
| ------- | -------- | ----------------------- |
| 参数列表    | 必须修改     | 一定不能修改                  |
| 返回类型    | 可以修改     | 一定不能修改                  |
| 异常      | 可以修改     | 可以减少或删除，一定不能抛出新的或者更广的异常 |
| 访问      | 可以修改     | 一定不能做更严格的限制（可以降低限制）     |

方法的重写(Overriding)和重载(Overloading)是java多态性的不同表现，重写是父类与子类之间多态性的一种表现，重载可以理解成多态的具体表现形式。

1. 方法重载是一个类中定义了多个方法名相同,而他们的参数的数量不同或数量相同而类型和次序不同,则称为方法的重载(Overloading)。
2. 方法重写是在子类存在方法与父类的方法的名字相同,而且参数的个数与类型一样,返回值也一样的方法,就称为重写(Overriding)。
3. 方法重载是一个类的多态性表现,而方法重写是子类与父类的一种多态性表现。

![](https://cdn.nlark.com/yuque/0/2023/png/28161567/1683199400077-d091365b-192d-4db3-b685-8a4516dbf2da.png)

## 接口 <a href="#qd1jh" id="qd1jh"></a>

接口（英文：Interface），在JAVA编程语言中是一个抽象类型，是抽象方法的集合，接口通常以interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。

接口并不是类，编写接口的方式和类很相似，但是它们属于不同的概念。类描述对象的属性和方法。接口则包含类要实现的方法。

除非实现接口的类是抽象类，否则该类要定义接口中的所有方法。

接口无法被实例化，但是可以被实现。一个实现接口的类，必须实现接口内所描述的所有方法，否则就必须声明为抽象类。另外，在 Java 中，接口类型可用来声明一个变量，他们可以成为一个空指针，或是被绑定在一个以此接口实现的对象。

### 接口与类相似点： <a href="#mvjkx" id="mvjkx"></a>

* 一个接口可以有多个方法。
* 接口文件保存在 .java 结尾的文件中，文件名使用接口名。
* 接口的字节码文件保存在 .class 结尾的文件中。
* 接口相应的字节码文件必须在与包名称相匹配的目录结构中。

### 接口与类的区别： <a href="#w5btx" id="w5btx"></a>

* 接口不能用于实例化对象。
* 接口没有构造方法。
* 接口中所有的方法必须是抽象方法。
* 接口不能包含成员变量，除了 static 和 final 变量。
* 接口不是被类继承了，而是要被类实现。
* 接口支持多继承。

### 接口特性 <a href="#jzqwn" id="jzqwn"></a>

* 接口中每一个方法也是隐式抽象的,接口中的方法会被隐式的指定为 **public abstract**（只能是 public abstract，其他修饰符都会报错）。
* 接口中可以含有变量，但是接口中的变量会被隐式的指定为 **public static final** 变量（并且只能是 public，用 private 修饰会报编译错误）。
* 接口中的方法是不能在接口中实现的，只能由实现接口的类来实现接口中的方法。

### 抽象类和接口的区别 <a href="#z7cnb" id="z7cnb"></a>

* 抽象类中的方法可以有方法体，就是能实现方法的具体功能，但是接口中的方法不行。
* 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是 **public static final** 类型的。
* 接口中不能含有静态代码块以及静态方法(用 static 修饰的方法)，而抽象类是可以有静态代码块和静态方法。
* 一个类只能继承一个抽象类，而一个类却可以实现多个接口。

### 接口的声明 <a href="#r0aib" id="r0aib"></a>

```
[可见度] interface 接口名称 [extends 其他的接口名] {
        // 声明变量
        // 抽象方法
}
```

Interface关键字用来声明一个接口。

```
import java.lang.*;
//引入包
 
public interface NameOfInterface {
   //任何类型 final, static 字段
   //抽象方法
}
```

接口有以下特性：

* 接口是隐式抽象的，当声明一个接口的时候，不必使用**abstract**关键字。
* 接口中每一个方法也是隐式抽象的，声明时同样不需要**abstract**关键字。
* 接口中的方法都是公有的。

```
interface Animal {
   public void eat();
   public void travel();
}
```

### 接口的实现 <a href="#wfg0y" id="wfg0y"></a>

当类实现接口的时候，类要实现接口中所有的方法。否则，类必须声明为抽象的类。

类使用implements关键字实现接口。在类声明中，Implements关键字放在class声明后面。

实现一个接口的语法，可以使用这个公式：

```
...implements 接口名称[, 其他接口名称, 其他接口名称..., ...] ...
```

#### 实例 <a href="#tjcvm" id="tjcvm"></a>

```
public class MammalInt implements Animal{
 
   public void eat(){
      System.out.println("Mammal eats");
   }
 
   public void travel(){
      System.out.println("Mammal travels");
   }
 
   public int noOfLegs(){
      return 0;
   }
 
   public static void main(String args[]){
      MammalInt m = new MammalInt();
      m.eat();
      m.travel();
   }
}
```

以上实例编译运行结果如下:

```
Mammal eats
Mammal travels
```

重写接口中声明的方法时，需要注意以下规则：

* 类在实现接口的方法时，不能抛出强制性异常，只能在接口中，或者继承接口的抽象类中抛出该强制性异常。
* 类在重写方法时要保持一致的方法名，并且应该保持相同或者相兼容的返回值类型。
* 如果实现接口的类是抽象类，那么就没必要实现该接口的方法。

在实现接口的时候，也要注意一些规则：

* 一个类可以同时实现多个接口。
* 一个类只能继承一个类，但是能实现多个接口。
* 一个接口能继承另一个接口，这和类之间的继承比较相似。

### 接口的继承 <a href="#fln7j" id="fln7j"></a>

一个接口能继承另一个接口，和类之间的继承方式比较相似。接口的继承使用extends关键字，子接口继承父接口的方法。

下面的Sports接口被Hockey和Football接口继承：

```
// 文件名: Sports.java
public interface Sports {
   public void setHomeTeam(String name);
   public void setVisitingTeam(String name);
}
 
// 文件名: Football.java
public interface Football extends Sports {
   public void homeTeamScored(int points);
   public void visitingTeamScored(int points);
   public void endOfQuarter(int quarter);
}
 
// 文件名: Hockey.java
public interface Hockey extends Sports {
   public void homeGoalScored();
   public void visitingGoalScored();
   public void endOfPeriod(int period);
   public void overtimePeriod(int ot);
}
```

Hockey接口自己声明了四个方法，从Sports接口继承了两个方法，这样，实现Hockey接口的类需要实现六个方法。

相似的，实现Football接口的类需要实现五个方法，其中两个来自于Sports接口。

### 接口的多继承 <a href="#rjihy" id="rjihy"></a>

在Java中，类的多继承是不合法，但接口允许多继承。

在接口的多继承中extends关键字只需要使用一次，在其后跟着继承接口。 如下所示：

```
public interface Hockey extends Sports, Event
```

以上的程序片段是合法定义的子接口，与类不同的是，接口允许多继承，而 Sports及 Event 可能定义或是继承相同的方法

### 标记接口 <a href="#snevk" id="snevk"></a>

最常用的继承接口是没有包含任何方法的接口。

标记接口是没有任何方法和属性的接口.它仅仅表明它的类属于一个特定的类型,供其他代码来测试允许做一些事情。

标记接口作用：简单形象的说就是给某个对象打个标（盖个戳），使对象拥有某个或某些特权。

例如：java.awt.event 包中的 MouseListener 接口继承的 java.util.EventListener 接口定义如下：

```
package java.util;
public interface EventListener
{}
```

没有任何方法的接口被称为标记接口。标记接口主要用于以下两种目的：

* 建立一个公共的父接口：正如EventListener接口，这是由几十个其他接口扩展的Java API，你可以使用一个标记接口来建立一组接口的父接口。例如：当一个接口继承了EventListener接口，Java虚拟机(JVM)就知道该接口将要被用于一个事件的代理方案。
* 向一个类添加数据类型：这种情况是标记接口最初的目的，实现标记接口的类不需要定义任何接口方法(因为标记接口根本就没有方法)，但是该类通过多态性变成一个接口类型。

## Java 抽象类 <a href="#qzrea" id="qzrea"></a>

在面向对象的概念中，所有的对象都是通过类来描绘的，但是反过来，并不是所有的类都是用来描绘对象的，如果一个类中没有包含足够的信息来描绘一个具体的对象，这样的类就是抽象类。\
抽象类除了不能实例化对象之外，类的其它功能依然存在，成员变量、成员方法和构造方法的访问方式和普通类一样。\
由于抽象类不能实例化对象，所以抽象类必须被继承，才能被使用。也是因为这个原因，通常在设计阶段决定要不要设计抽象类。\
父类包含了子类集合的常见的方法，但是由于父类本身是抽象的，所以不能使用这些方法。\
在Java中抽象类表示的是一种继承关系，一个类只能继承一个抽象类，而一个类却可以实现多个接口。

### 抽象类 <a href="#wj4kb" id="wj4kb"></a>

在Java语言中使用abstract class来定义抽象类。如下实例：

```
public abstract class Employee {
   private String name;
   private String address;
   private int number;
   public Employee(String name, String address, int number) {
      System.out.println("Constructing an Employee");
      this.name = name;
      this.address = address;
      this.number = number;
   }
   public double computePay() {
     System.out.println("Inside Employee computePay");
     return 0.0;
   }
   public void mailCheck() {
      System.out.println("Mailing a check to " + this.name
       + " " + this.address);
   }
   public String toString() {
      return name + " " + address + " " + number;
   }
   public String getName() {
      return name;
   }
   public String getAddress() {
      return address;
   }
   public void setAddress(String newAddress) {
      address = newAddress;
   }
   public int getNumber() {
     return number;
   }
}
```

注意到该 Employee 类没有什么不同，尽管该类是抽象类，但是它仍然有 3 个成员变量，7 个成员方法和 1 个构造方法。 现在如果你尝试如下的例子：

```
public class AbstractDemo {
   public static void main(String [] args) {
      /* 以下是不允许的，会引发错误 */
      Employee e = new Employee("George W.", "Houston, TX", 43);

      System.out.println("\n Call mailCheck using Employee reference--");
      e.mailCheck();
    }
}
```

当你尝试编译AbstractDemo类时，会产生如下错误：

```
Employee.java:46: Employee is abstract; cannot be instantiated
      Employee e = new Employee("George W.", "Houston, TX", 43);
                   ^
1 error
```

### 继承抽象类 <a href="#b4uud" id="b4uud"></a>

我们能通过一般的方法继承Employee类：

```
public class Salary extends Employee {
   private double salary; //Annual salary
   public Salary(String name, String address, int number, double salary) {
       super(name, address, number);
       setSalary(salary);
   }
   public void mailCheck() {
       System.out.println("Within mailCheck of Salary class ");
       System.out.println("Mailing check to " + getName()
       + " with salary " + salary);
   }
   public double getSalary() {
       return salary;
   }
   public void setSalary(double newSalary) {
       if(newSalary >= 0.0) {
          salary = newSalary;
       }
   }
   public double computePay() {
      System.out.println("Computing salary pay for " + getName());
      return salary/52;
   }
}
```

尽管我们不能实例化一个 Employee 类的对象，但是如果我们实例化一个 Salary 类对象，该对象将从 Employee 类继承 7 个成员方法，且通过该方法可以设置或获取三个成员变量。

```
public class AbstractDemo {
   public static void main(String [] args) {
      Salary s = new Salary("Mohd Mohtashim", "Ambehta, UP", 3, 3600.00);
      Employee e = new Salary("John Adams", "Boston, MA", 2, 2400.00);

      System.out.println("Call mailCheck using Salary reference --");
      s.mailCheck();

      System.out.println("\n Call mailCheck using Employee reference--");
      e.mailCheck();
    }
}
```

```
Constructing an Employee
Constructing an Employee
Call mailCheck using  Salary reference --
Within mailCheck of Salary class
Mailing check to Mohd Mohtashim with salary 3600.0

Call mailCheck using Employee reference--
Within mailCheck of Salary class
Mailing check to John Adams with salary 2400.
```

### 抽象方法 <a href="#zbqlx" id="zbqlx"></a>

如果你想设计这样一个类，该类包含一个特别的成员方法，该方法的具体实现由它的子类确定，那么你可以在父类中声明该方法为抽象方法。

Abstract 关键字同样可以用来声明抽象方法，抽象方法只包含一个方法名，而没有方法体。

抽象方法没有定义，方法名后面直接跟一个分号，而不是花括号。

```
public abstract class Employee {
   private String name;
   private String address;
   private int number;

   public abstract double computePay();

   //其余代码
}
```

声明抽象方法会造成以下两个结果：

* 如果一个类包含抽象方法，那么该类必须是抽象类。
* 任何子类必须重写父类的抽象方法，或者声明自身为抽象类。

继承抽象方法的子类必须重写该方法。否则，该子类也必须声明为抽象类。最终，必须有子类实现该抽象方法，否则，从最初的父类到最终的子类都不能用来实例化对象。

如果Salary类继承了Employee类，那么它必须实现computePay()方法：

```
public class Salary extends Employee {
   private double salary; // Annual salary

   public double computePay() {
      System.out.println("Computing salary pay for " + getName());
      return salary/52;
   }

   //其余代码
}
```

### 抽象类总结规定 <a href="#wi9hb" id="wi9hb"></a>

* 抽象类不能被实例化(初学者很容易犯的错)，如果被实例化，就会报错，编译无法通过。只有抽象类的非抽象子类可以创建对象。
* 抽象类中不一定包含抽象方法，但是有抽象方法的类必定是抽象类。
* 抽象类中的抽象方法只是声明，不包含方法体，就是不给出方法的具体实现也就是方法的具体功能。
* 构造方法，类方法（用 static 修饰的方法）不能声明为抽象方法。
* 抽象类的子类必须给出抽象类中的抽象方法的具体实现，除非该子类也是抽象类。

## Java 异常处理 <a href="#hwxj8" id="hwxj8"></a>

异常是程序中的一些错误，但并不是所有的错误都是异常，并且错误有时候是可以避免的。

比如说，你的代码少了一个分号，那么运行出来结果是提示是错误 java.lang.Error；如果你用System.out.println(11/0)，那么你是因为你用0做了除数，会抛出 java.lang.ArithmeticException 的异常。

异常发生的原因有很多，通常包含以下几大类：

* 用户输入了非法数据。
* 要打开的文件不存在。
* 网络通信时连接中断，或者JVM内存溢出。

这些异常有的是因为用户错误引起，有的是程序错误引起的，还有其它一些是因为物理错误引起的。-

要理解Java异常处理是如何工作的，你需要掌握以下三种类型的异常：

* **检查性异常：**最具代表的检查性异常是用户错误或问题引起的异常，这是程序员无法预见的。例如要打开一个不存在文件时，一个异常就发生了，这些异常在编译时不能被简单地忽略。
* **运行时异常：** 运行时异常是可能被程序员避免的异常。与检查性异常相反，运行时异常可以在编译时被忽略。
* **错误：** 错误不是异常，而是脱离程序员控制的问题。错误在代码中通常被忽略。例如，当栈溢出时，一个错误就发生了，它们在编译也检查不到的。

### Exception 类的层次 <a href="#rycgk" id="rycgk"></a>

所有的异常类是从 java.lang.Exception 类继承的子类。

Exception 类是 Throwable 类的子类。除了Exception类外，Throwable还有一个子类Error 。

Java 程序通常不捕获错误。错误一般发生在严重故障时，它们在Java程序处理的范畴之外。

Error 用来指示运行时环境发生的错误。

例如，JVM 内存溢出。一般地，程序不会从错误中恢复。

异常类有两个主要的子类：IOException 类和 RuntimeException 类。

![](https://cdn.nlark.com/yuque/0/2023/jpeg/28161567/1683550155420-ea19524d-c5f5-47ec-9167-2bf933a40b3c.jpeg)

在 Java 内置类中(接下来会说明)，有大部分常用检查性和非检查性异常。

### Java 内置异常类 <a href="#zfwf6" id="zfwf6"></a>

Java 语言定义了一些异常类在 java.lang 标准包中。

标准运行时异常类的子类是最常见的异常类。由于 java.lang 包是默认加载到所有的 Java 程序的，所以大部分从运行时异常类继承而来的异常都可以直接使用。

Java 根据各个类库也定义了一些其他的异常，下面的表中列出了 Java 的非检查性异常。

| **异常**                          | **描述**                                                           |
| ------------------------------- | ---------------------------------------------------------------- |
| ArithmeticException             | 当出现异常的运算条件时，抛出此异常。例如，一个整数"除以零"时，抛出此类的一个实例。                       |
| ArrayIndexOutOfBoundsException  | 用非法索引访问数组时抛出的异常。如果索引为负或大于等于数组大小，则该索引为非法索引。                       |
| ArrayStoreException             | 试图将错误类型的对象存储到一个对象数组时抛出的异常。                                       |
| ClassCastException              | 当试图将对象强制转换为不是实例的子类时，抛出该异常。                                       |
| IllegalArgumentException        | 抛出的异常表明向方法传递了一个不合法或不正确的参数。                                       |
| IllegalMonitorStateException    | 抛出的异常表明某一线程已经试图等待对象的监视器，或者试图通知其他正在等待对象的监视器而本身没有指定监视器的线程。         |
| IllegalStateException           | 在非法或不适当的时间调用方法时产生的信号。换句话说，即 Java 环境或 Java 应用程序没有处于请求操作所要求的适当状态下。 |
| IllegalThreadStateException     | 线程没有处于请求操作所要求的适当状态时抛出的异常。                                        |
| IndexOutOfBoundsException       | 指示某排序索引（例如对数组、字符串或向量的排序）超出范围时抛出。                                 |
| NegativeArraySizeException      | 如果应用程序试图创建大小为负的数组，则抛出该异常。                                        |
| NullPointerException            | 当应用程序试图在需要对象的地方使用 null 时，抛出该异常                                   |
| NumberFormatException           | 当应用程序试图将字符串转换成一种数值类型，但该字符串不能转换为适当格式时，抛出该异常。                      |
| SecurityException               | 由安全管理器抛出的异常，指示存在安全侵犯。                                            |
| StringIndexOutOfBoundsException | 此异常由 String 方法抛出，指示索引或者为负，或者超出字符串的大小。                            |
| UnsupportedOperationException   | 当不支持请求的操作时，抛出该异常。                                                |

下面的表中列出了 Java 定义在 java.lang 包中的检查性异常类。

| **异常**                     | **描述**                                                                     |
| -------------------------- | -------------------------------------------------------------------------- |
| ClassNotFoundException     | 应用程序试图加载类时，找不到相应的类，抛出该异常。                                                  |
| CloneNotSupportedException | 当调用 Object 类中的 clone 方法克隆对象，但该对象的类无法实现 Cloneable 接口时，抛出该异常。                |
| IllegalAccessException     | 拒绝访问一个类的时候，抛出该异常。                                                          |
| InstantiationException     | 当试图使用 Class 类中的 newInstance 方法创建一个类的实例，而指定的类对象因为是一个接口或是一个抽象类而无法实例化时，抛出该异常。 |
| InterruptedException       | 一个线程被另一个线程中断，抛出该异常。                                                        |
| NoSuchFieldException       | 请求的变量不存在                                                                   |
| NoSuchMethodException      | 请求的方法不存在                                                                   |

### 异常方法 <a href="#qxrfu" id="qxrfu"></a>

下面的列表是 Throwable 类的主要方法:

| **序号** | **方法及说明**                                                                                     |
| ------ | --------------------------------------------------------------------------------------------- |
| 1      | **public String getMessage()** 返回关于发生的异常的详细信息。这个消息在Throwable 类的构造函数中初始化了。                     |
| 2      | **public Throwable getCause()** 返回一个Throwable 对象代表异常原因。                                       |
| 3      | **public String toString()** 使用getMessage()的结果返回类的串级名字。                                       |
| 4      | **public void printStackTrace()** 打印toString()结果和栈层次到System.err，即错误输出流。                       |
| 5      | **public StackTraceElement \[] getStackTrace()** 返回一个包含堆栈层次的数组。下标为0的元素代表栈顶，最后一个元素代表方法调用堆栈的栈底。 |
| 6      | **public Throwable fillInStackTrace()** 用当前的调用栈层次填充Throwable 对象栈层次，添加到栈层次任何先前信息中。             |

### 捕获异常 <a href="#bfza3" id="bfza3"></a>

使用 try 和 catch 关键字可以捕获异常。try/catch 代码块放在异常可能发生的地方。

try/catch代码块中的代码称为保护代码，使用 try/catch 的语法如下：

```
try {
   // 程序代码
}catch(ExceptionName e1) {
   //Catch 块
}
```

Catch 语句包含要捕获异常类型的声明。当保护代码块中发生一个异常时，try 后面的 catch 块就会被检查。

如果发生的异常包含在 catch 块中，异常会被传递到该 catch 块，这和传递一个参数到方法是一样。

#### 实例 <a href="#ldxut" id="ldxut"></a>

下面的例子中声明有两个元素的一个数组，当代码试图访问数组的第三个元素的时候就会抛出一个异常。

```
// 文件名 : ExcepTest.java
import java.io.*;
public class ExcepTest{

   public static void main(String args[]){
      try{
         int a[] = new int[2];
         System.out.println("Access element three :" + a[3]);
      }catch(ArrayIndexOutOfBoundsException e){
         System.out.println("Exception thrown  :" + e);
      }
      System.out.println("Out of the block");
   }
}
```

以上代码编译运行输出结果如下：

```
Exception thrown  :java.lang.ArrayIndexOutOfBoundsException: 3
Out of the block
```

### 多重捕获块 <a href="#okwps" id="okwps"></a>

一个 try 代码块后面跟随多个 catch 代码块的情况就叫多重捕获。

多重捕获块的语法如下所示：

```
try{
   // 程序代码
}catch(异常类型1 异常的变量名1){
  // 程序代码
}catch(异常类型2 异常的变量名2){
  // 程序代码
}catch(异常类型2 异常的变量名2){
  // 程序代码
}
```

上面的代码段包含了 3 个 catch块。

可以在 try 语句后面添加任意数量的 catch 块。

如果保护代码中发生异常，异常被抛给第一个 catch 块。

如果抛出异常的数据类型与 ExceptionType1 匹配，它在这里就会被捕获。

如果不匹配，它会被传递给第二个 catch 块。

如此，直到异常被捕获或者通过所有的 catch 块。

#### 实例 <a href="#s9c8k" id="s9c8k"></a>

该实例展示了怎么使用多重 try/catch。

```
public class DivideByZeroExample {
    public static void main(String[] args) {
        int a = 10, b = 0;

        try {
            int c = a / b; // 可能会抛出异常
        } catch (ArithmeticException e) { // 异常类型为 ArithmeticException
            System.out.println("除数为0，导致无法计算。");
        } catch (Exception e) { // 异常类型为 Exception，可以处理任意类型的异常
            System.out.println("未知异常：" + e.getMessage());
        }

        System.out.println("程序结束。");
    }
}
```

```
除数为0，导致无法计算。
程序结束。
```

### throws/throw 关键字： <a href="#cuine" id="cuine"></a>

如果一个方法没有捕获到一个检查性异常，那么该方法必须使用 throws 关键字来声明。throws 关键字放在方法签名的尾部。

也可以使用 throw 关键字抛出一个异常，无论它是新实例化的还是刚捕获到的。

下面方法的声明抛出一个 RemoteException 异常：

```
import java.io.*;
public class className {
    public void deposit(double amount) throws RemoteException {
        // Method implementation
        throw new RemoteException();
    }
    //Remainder of class definition
}
```

一个方法可以声明抛出多个异常，多个异常之间用逗号隔开。

例如，下面的方法声明抛出 RemoteException 和 InsufficientFundsException：

```
import java.io.*;
public class className {
    public void withdraw(double amount) throws RemoteException,
            InsufficientFundsException {
        // Method implementation
    }
    //Remainder of class definition
}
```

### finally关键字 <a href="#ovqai" id="ovqai"></a>

finally 关键字用来创建在 try 代码块后面执行的代码块。

无论是否发生异常，finally 代码块中的代码总会被执行。

在 finally 代码块中，可以运行清理类型等收尾善后性质的语句。

finally 代码块出现在 catch 代码块最后，语法如下：

```
try{
  // 程序代码
}catch(异常类型1 异常的变量名1){
  // 程序代码
}catch(异常类型2 异常的变量名2){
  // 程序代码
}finally{
  // 程序代码
}
```

#### 实例 <a href="#q5tbf" id="q5tbf"></a>

```
public class ExcepTest {
    public static void main(String[] args) {
        int[] a = new int[2];
        try {
            System.out.println("Access element three :" + a[3]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Exception thrown  :" + e);
        } finally {
            a[0] = 6;
            assert System.out != null;
            System.out.println("First element value: " + a[0]);
            System.out.println("The finally statement is executed");
        }
    }
}
```

以上实例编译运行结果如下：

```
Exception thrown  :java.lang.ArrayIndexOutOfBoundsException: 3
First element value: 6
The finally statement is executed
```

注意下面事项：

* catch 不能独立于 try 存在。
* 在 try/catch 后面添加 finally 块并非强制性要求的。
* try 代码后不能既没 catch 块也没 finally 块。
* try, catch, finally 块之间不能添加任何代码。

### 声明自定义异常 <a href="#kaofl" id="kaofl"></a>

在 Java 中你可以自定义异常。编写自己的异常类时需要记住下面的几点。

* 所有异常都必须是 Throwable 的子类。
* 如果希望写一个检查性异常类，则需要继承 Exception 类。
* 如果你想写一个运行时异常类，那么需要继承 RuntimeException 类。

可以像下面这样定义自己的异常类：

```
class MyException extends Exception{
	
}
```

只继承Exception 类来创建的异常类是检查性异常类。

下面的 InsufficientFundsException 类是用户定义的异常类，它继承自 Exception。

一个异常类和其它任何类一样，包含有变量和方法。

#### 实例 <a href="#kajai" id="kajai"></a>

以下实例是一个银行账户的模拟，通过银行卡的号码完成识别，可以进行存钱和取钱的操作。

```
// 文件名InsufficientFundsException.java

//自定义异常类，继承Exception类
public class InsufficientFundsException extends Exception {
    //此处的amount用来储存当出现异常（取出钱多于余额时）所缺乏的钱
    private double amount;

    public InsufficientFundsException(double amount) {
        this.amount = amount;
    }

    public double getAmount() {
        return amount;
    }
}
```

为了展示如何使用我们自定义的异常类，

在下面的 CheckingAccount 类中包含一个 withdraw() 方法抛出一个 InsufficientFundsException 异常。

```
// 文件名称 CheckingAccount.java

//此类模拟银行账户
public class CheckingAccount {
    //balance为余额，number为卡号
    private double balance;
    private int number;

    public CheckingAccount(int number) {
        this.number = number;
    }

    //方法：存钱
    public void deposit(double amount) {
        balance += amount;
    }

    //方法：取钱
    public void withdraw(double amount) throws
            InsufficientFundsException {
        if (amount <= balance) {
            balance -= amount;
        } else {
            double needs = amount - balance;
            throw new InsufficientFundsException(needs);
        }
    }

    //方法：返回余额
    public double getBalance() {
        return balance;
    }

    //方法：返回卡号
    public int getNumber() {
        return number;
    }
}
```

下面的 BankDemo 程序示范了如何调用 CheckingAccount 类的 deposit() 和 withdraw() 方法。

```
//文件名称 BankDemo.java
public class BankDemo {
    public static void main(String[] args) {
        CheckingAccount c = new CheckingAccount(101);
        System.out.println("Depositing $500...");
        c.deposit(500.00);
        try {
            System.out.println("\nWithdrawing $100...");
            c.withdraw(100.00);
            System.out.println("\nWithdrawing $600...");
            c.withdraw(600.00);
        } catch (InsufficientFundsException e) {
            System.out.println("Sorry, but you are short $"
                    + e.getAmount());
            e.printStackTrace();
        }
    }
}
```

编译上面三个文件，并运行程序 BankDemo，得到结果如下所示：

```
Depositing $500...

Withdrawing $100...

Withdrawing $600...
Sorry, but you are short $200.0
InsufficientFundsException
        at CheckingAccount.withdraw(CheckingAccount.java:25)
        at BankDemo.main(BankDemo.java:13)
```

### 通用异常 <a href="#bz4lg" id="bz4lg"></a>

在Java中定义了两种类型的异常和错误。

* **JVM(Java虚拟机)** **异常：**由 JVM 抛出的异常或错误。例如：NullPointerException 类，ArrayIndexOutOfBoundsException 类，ClassCastException 类。
* **程序级异常：**由程序或者API程序抛出的异常。例如 IllegalArgumentException 类，IllegalStateException 类。

## **final** <a href="#yzflc" id="yzflc"></a>

Java 中的 final 关键字是一个修饰符，它可以用于修饰四种不同的目标：

### 类 <a href="#ztbp3" id="ztbp3"></a>

```
final class MyClass {
    // ...
}
```

用 final 修饰的类表示它是一个不能被继承的最终类。例如，Java 标准类库中的 String 类就是一个用 final 修饰的类，所以在继承它时会直接编译报错。

### 方法 <a href="#qufdv" id="qufdv"></a>

```
class MyClass {
    final void myMethod() {
        // ...
    }
}
```

用 final 修饰的方法表示它是一个不能被子类重写的最终方法。例如，Java 标准类库中的 Object 类中的 getClass() 方法就是一个用 final 修饰的方法。

### &#x20;<a href="#xx38f" id="xx38f"></a>

### 变量 <a href="#lmtam" id="lmtam"></a>

```
class MyClass {
    final int x = 10;
}
```

用 final 修饰的变量表示它是一个常量，一旦被初始化后就不能再被修改。例如，Java 中的数学常量 pi 就可以这样定义：final double PI = 3.1415926;。

除了用 final 关键字修饰变量之外，还可以用 static 关键字和 final 关键字联合修饰一个类变量来表示一个类级别的常量。例如：

```
class MyClass {
    static final double PI = 3.1415926;
}
```

这里的 PI 变量是属于 MyClass 类的，因此在其它的地方可以通过 MyClass.PI 的方式来访问它。

### 参数 <a href="#mxfmt" id="mxfmt"></a>

```
class MyClass {
    void myMethod(final int x) {
  	// ...
    }
}
```

用 final 修饰方法参数表示它是一个只读的参数，一旦在方法内部被赋值，就不能再修改该参数的值了。

final 修饰符的主要作用是在提高代码的安全性、可读性、维护性和效率方面。例如，用 final 修饰的常量可以减少代码中的魔数（magic number），从而提高代码的可读性；用 final 修饰的方法和类可以提高代码的安全性，因为它们不能被子类修改或重写；而用 final 修饰方法参数可以帮助程序员确定参数的使用范围，避免程序出现意外或者出错。
