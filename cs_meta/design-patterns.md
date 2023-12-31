# Design Patterns



## 概念

* 什么是设计模式
  * 软件设计中普遍存在（反复出现）的各种问题，所提出的通用解决方案。
  * 系统地命名、解释、评价这些重复出现的设计。



* GoF介绍
  * Gang of Four的简称
  * Erich Gamma，Richard Helm，Ralph Johnson，John Vlissides，四个人
  * 共同写作《设计模式：可复用面向对象软件的基础》



* 面向对象与设计模式的联系
  * 设计模式总结的是面向对象思想下的通用解决方案



* 什么是面向对象
  * OO，object-oriented
  * 程序被组织成对象的集合，每个对象都包含了数据和操作数据的函数



* 面向对象的三大特性
  * 封装
    * 函数
    * 类
    * 属性作用域，私有、公有
  * 继承
  * 多态，同一个方法可以在不同的类中有不同的实现方式
    * C++虚函数和普通函数
    * Java通过接口和继承实现
    * Python通过鸭子类型实现，即反射，查找相同名称的属性
    * JS通过原型链实现



* 什么是接口
  * 若干抽象方法的集合
  * Python支持多重继承，可以通过继承抽象基类实现



* 接口的作用
  * 限制实现接口的类必须按照接口给定的调用方式实现
  * 对高层模块隐藏了类的内部实现
  * 例如支付接口
    * 上层模块调用支付接口，无需关心细节
    * 底层模块实现各种支付接口，无需修改上层



* python中实现接口
  * `metaclass=ABCMeta`的类，不能直接实例化，必须继承后实例化
  * 使用`abstractmethod`装饰器修饰函数，不能直接调用，必须实现后才能调用

```python
from abc import ABCMeta
from abc import abstractmethod

class C(metaclass=ABCMeta):
    @abstractmethod
    def func(self):
       	pass
```





## 设计原则

* SOLID原则
  * SRP，Single Responsibility Principle，单一职责原则
  * OCP，Open Close Principle，开放封闭原则
  * LSP，Liskov Substitution Principle，里氏替换原则
  * ISP，Interface Segregation Principle，接口隔离原则
  * DIP，Dependence Inversion Principle，依赖倒置原则



* 单一职责原则，Single Responsibility Principle
  * 一个类只负责一项职责
  * 或者说，一个类应该只有一个引起它变化的原因
  * 或者说，不要存在多余一个导致类变更的原因



* 开放封闭原则，Open Close Principle
  * 对扩展开放，对修改关闭
  * 软件实体（类、模块、函数）应尽量在不修改原有代码的情况下进行扩展



* 里氏代换原则，Liskov Substitution Principle
  * 所有引用父类的地方必须能透明地使用其子类对象。
  * 只有当衍生类可以替换掉基类，软件单位的功能不受到影响时，基类才能真正被复用，而衍生类也能够在基类的基础上增加新的行为。



* 接口隔离原则，Interface Segregation Principle
  * 使用多个隔离的接口来降低耦合度
  * 使用多个专门的接口，而不使用单一的总接口
  * 即客户端不应该依赖那些它不需要的接口
  * 例如，将抽象动物类拆分为抽象鸟类、抽象爬行动物类，不要使用一个多合一的抽象动物类



* 依赖倒转原则，Dependence Inversion Principle
  * 是开闭原则的基础，针对接口编程，而不是针对实现编程
  * 高层模块不应该依赖底层模块，二者都应该依赖其抽象
  * 或者说，抽象不应该依赖细节；细节应该依赖抽象



* 迪米特法则，Demeter Principle
  * 一个实体应当尽量少的与其他实体之间发生相互作用，使得系统功能模块相对独立。



* 合成复用原则，Composite Reuse Principle
  * 尽量使用合成/聚合的方式，而不是使用继承。继承实际上破坏了类的封装性，超类的方法可能会被子类修改。



## UML
* Unified Modeling Language, 统一建模语言
* 结构性图：
    * 类图
    * 组件图
    * 部署图
    * 对象图
    * 包图
    * 组合结构图
    * 轮廓图
* 行为性图：
    * 用例图
    * 活动图（流程图）
    * 状态机图
    * 序列图
    * 通信图
    * 交互图
    * 时序图
* 类图（从强到弱排序）：
    * 泛化 Generalization：继承关系
    * 实现 Realization：结构关系
    * 组合 Composition：整体与不可或缺部分， 
    * 聚合 Aggreggation：整体与单独存在部分，
    * 关联 Association：拥有关系，知道另一个类存在，可以双向
    * 依赖 Dependency：使用关系，需要另一个类协助，尽量不要循环依赖
* 类图（标记）：
    * 泛化: 特殊 实线三角指向 一般
    * 实现: 实现 虚线三角指向 接口
    * 组合: 部分 实线实心菱形指向 整体
    * 聚合: 部分 实线空心菱形指向 整体
    * 关联: 拥有者 实线箭头指向 被拥有者
    * 依赖: 使用者 虚线箭头指向 被使用者



## 创建类模式

* 什么是创建类模式
  * 创建对象时用到的模式



## 创建类 - 单例模式

* 定义
  * 保证一个类仅有一个实例，并提供一个访问它的全局访问点



* 使用场景
  * 生成全局唯一的序列号。
  * 访问全局复用的唯一资源，如磁盘，总线。
  * 单个对象占用资源过多，如数据库。
  * 系统全局统一管理，如Task Manager。
  * 网站计数器。



* 角色
  * 单例，Singleton



* 优点
    * 全局仅一个实例，节省内存空间
    * 全局只有一个接入点，可以更好进行同步控制，避免多重占用。
    * 可以常驻内存，减少系统开销



* 缺点
    * 扩展困难
    * 违反单一职责原则
    * 在并发模块中需要最先完成，不利于测试。
    * 会导致资源瓶颈。



* 分类

  * 懒汉式：使用时才创建（会产生并发可重入问题）

  * 饿汉式：启动时创建




* python单例
  * python模块本身就是单例的，模块名相同，不会二次导入模块



### Python元类与类装饰器

* 指定元类
  * 定义类时使用`metaclass`参数指定元类
  * 定义类时使用`__metaclass__`属性指定元类，Python3已废弃



* 元类与类的`__new__`、`__init__`、`__call__`对比

  * `Meta.__new__(cls, name, bases, attrs)`
    * 调用时机：创建类之前，只调用一次
    * 用途：修改类属性`attrs`
    * 入参：类名、父类列表、属性列表
    * 返回值：创建的类，Meta的父类构建的对象
  * `Meta.__init__(cls, name, bases, attrs)`
    * 调用时机：创建类之后，只调用一次
    * 用途：初始化类属性`attrs`，无法修改`attrs`
    * 入参：`Meta.__new__(cls, name, bases, attrs)`中修改后调用`super().__new__(cls, name, bases, attrs)`传入的类名、父类列表、属性列表
    * 返回值：无
  * `Meta.__call__(cls, *args, **kwargs)`
    * 调用时机：创建类之后，每次创建类实例之前
    * 用途：自定义实例化过程，修改类的实例的参数、行为
    * 入参：用户实例化类时传入，修改或透传给`Class.__new__(cls, *args, **kwargs)`
    * 返回值：实例化的对象，Metaclass的父类构建的对象
  * `Class.__new__(cls, *args, **kwargs)`
    * 调用时机：每次创建实例之前
    * 用途：在实例化之前做一些操作，干预对象的构建
    * 入参：用户实例化类时传入，在`Metaclass.__call__`中修改或透传的
    * 返回值：实例化的对象，Class的父类构建的对象
  * `Class.__init__(self, *args, **kwargs)`
    * 调用时机：每次创建实例之后
    * 用途：在实例化之后做一些工作，干预对象，如初始化
    * 入参：自定义
    * 返回值：无

  * `Class.__call__(self)`
    * 调用时机：用户主动调用对象时
    * 用途：实现`callable`对象，使得对象可以使用函数调用操作符
    * 入参：用户自定义
    * 返回值：用户自定义




* 类构建的过程
  * `读取类的定义` 
  * -> `Meta.__new__` -> `Meta父类.__new__`
  * -> `调用Python内核构建类` 
  * -> `Meta.__init__` -> `Meta父类.__init__`
  * -> `类构建完成`
  * -> `读取装饰器`



* 对象创建的过程
  * `读取对象的创建参数` 
  * `执行装饰器返回的包装对象`
  * -> `Meta.__call__ 前` -> `Meta父类.__call__`
  * -> `Class.__new__` -> `Class父类.__new__` 
  * -> `调用Python内核构建对象` 
  * -> `Class.__init__` -> `Class父类.__init__`
  * -> `Meta.__call__ 后`



* 调用父类的方法

  * 单继承使用`super()`调用父类方法
    * `super().__init__()`，不需要传`self`

  * 多继承使用`super()`调用父类方法
    * `super(父类, self).__init__()`，不需要传`self`
  * 显示调用父类方法
    * `父类.__init__(self, param)`，需要传`self`



* 测试

```py
from icecream import ic


class Meta(type):
    def __new__(cls, name, bases, attrs):
        ic('Meta.__new__ 前', cls, name, bases, attrs)

        # 添加类属性
        attrs['Meta_new_attr'] = None

        # 调用父类 __new__
        tmp = super().__new__(cls, name, bases, attrs)

        # 返回创建的类
        ic('Meta.__new__ 后', type(tmp), tmp)
        return tmp

    def __init__(cls, name, bases, attrs):
        ic('Meta.__init__ 前', cls, name, bases, attrs)

        # 添加类属性无效，类已经创建完成
        attrs['Meta_init_attr'] = None

        # 调用父类
        super().__init__(name, bases, attrs)

        # 不需要返回值
        ic('Meta.__init__ 后')

    def __call__(cls, *args, **kwargs):
        ic('Meta.__call__ 前', cls, args, kwargs)

        # 修改创建对象的参数
        kwargs['Meta_call_kwarg'] = None

        # 调用父类
        tmp = super().__call__(*args, **kwargs)

        # 返回
        ic('Meta.__call__ 后', type(tmp), tmp)
        return tmp


def class_decorator(cls):
    ic('class_decorator 前', cls)

    def class_decorator_new(*args, **kwargs):
        ic('class_decorator_new 前', cls, args, kwargs)

        kwargs['class_decorator_new_kwargs'] = None

        obj = cls(*args, **kwargs)

        ic('class_decorator_new 后', type(obj), obj)
        return obj

    return class_decorator_new


@class_decorator
class Cls(metaclass=Meta):
    Class_define_attr = None

    def __new__(cls, *args, **kwargs):
        ic('Class.__new__ 前', cls, args, kwargs)

        kwargs['Class_new_kwarg'] = None

        # 调用父类
        # 父类是Object，不再需要参数
        # 父类是其他，可能需要参数
        tmp = super().__new__(cls)

        # 返回对象
        ic('Class.__new__ 后', type(tmp), tmp)
        return tmp

    def __init__(self, *args, **kwargs):
        ic('Class.__init__ 前', self, args, kwargs)

        # 添加对象创建属性无效，对象已经创建完成
        kwargs['Class_init_kwarg'] = None

        # 调用父类
        # 父类是Object, 不再需要参数
        # 父类是其他，可能需要参数
        super().__init__()

        # 不需要返回值
        ic('Class.__init__ 后')

    def __call__(self):
        ic('用户主动调用函数执行操作符时')



a = Cls('用户创建对象参数1')
ic(a.Class_define_attr)
ic(a.Meta_new_attr)
# ic(a.Meta_init_attr)
b = Cls('用户创建对象参数2')
```



* 打印结果

```py
ic| 'Meta.__new__ 前': 'Meta.__new__ 前'
    cls: <class '__main__.Meta'>
    name: 'Cls'
    bases: ()
    attrs: {'Class_define_attr': None,
            '__call__': <function Cls.__call__ at 0x000002519E7DD3A0>,
            '__classcell__': <cell at 0x000002519DDCE430: empty>,
            '__init__': <function Cls.__init__ at 0x000002519E7DD310>,
            '__module__': '__main__',
            '__new__': <function Cls.__new__ at 0x000002519E7DD280>,
            '__qualname__': 'Cls'}
ic| 'Meta.__new__ 后': 'Meta.__new__ 后'
    type(tmp): <class '__main__.Meta'>
    tmp: <class '__main__.Cls'>
ic| 'Meta.__init__ 前': 'Meta.__init__ 前'
    cls: <class '__main__.Cls'>
    name: 'Cls'
    bases: ()
    attrs: {'Class_define_attr': None,
            'Meta_new_attr': None,
            '__call__': <function Cls.__call__ at 0x000002519E7DD3A0>,
            '__classcell__': <cell at 0x000002519DDCE430: Meta object at 0x000002519B9C7450>, 
            '__init__': <function Cls.__init__ at 0x000002519E7DD310>,
            '__module__': '__main__',
            '__new__': <function Cls.__new__ at 0x000002519E7DD280>,
            '__qualname__': 'Cls'}
ic| 'Meta.__init__ 后'
ic| 'class_decorator 前', cls: <class '__main__.Cls'>
ic| 'class_decorator_new 前': 'class_decorator_new 前'
    cls: <class '__main__.Cls'>
    args: ('用户创建对象参数1',)
    kwargs: {}
ic| 'Meta.__call__ 前': 'Meta.__call__ 前'
    cls: <class '__main__.Cls'>
    args: ('用户创建对象参数1',)
    kwargs: {'class_decorator_new_kwargs': None}
ic| 'Class.__new__ 前': 'Class.__new__ 前'
    cls: <class '__main__.Cls'>
    args: ('用户创建对象参数1',)
    kwargs: {'Meta_call_kwarg': None, 'class_decorator_new_kwargs': None}
ic| 'Class.__new__ 后': 'Class.__new__ 后'
    type(tmp): <class '__main__.Cls'>
    tmp: <__main__.Cls object at 0x000002519E869070>
ic| 'Class.__init__ 前': 'Class.__init__ 前'
    self: <__main__.Cls object at 0x000002519E869070>
    args: ('用户创建对象参数1',)
    kwargs: {'Meta_call_kwarg': None, 'class_decorator_new_kwargs': None}
ic| 'Class.__init__ 后'
ic| 'Meta.__call__ 后': 'Meta.__call__ 后'
    type(tmp): <class '__main__.Cls'>
    tmp: <__main__.Cls object at 0x000002519E869070>
ic| 'class_decorator_new 后': 'class_decorator_new 后'
    type(obj): <class '__main__.Cls'>
    obj: <__main__.Cls object at 0x000002519E869070>
ic| a.Class_define_attr: None
ic| a.Meta_new_attr: None
ic| 'class_decorator_new 前': 'class_decorator_new 前'
    cls: <class '__main__.Cls'>
    args: ('用户创建对象参数2',)
    kwargs: {}
ic| 'Meta.__call__ 前': 'Meta.__call__ 前'
    cls: <class '__main__.Cls'>
    args: ('用户创建对象参数2',)
    kwargs: {'class_decorator_new_kwargs': None}
ic| 'Class.__new__ 前': 'Class.__new__ 前'
    cls: <class '__main__.Cls'>
    args: ('用户创建对象参数2',)
    kwargs: {'Meta_call_kwarg': None, 'class_decorator_new_kwargs': None}
ic| 'Class.__new__ 后': 'Class.__new__ 后'
    type(tmp): <class '__main__.Cls'>
    tmp: <__main__.Cls object at 0x000002519F8FEB20>
ic| 'Class.__init__ 前': 'Class.__init__ 前'
    self: <__main__.Cls object at 0x000002519F8FEB20>
    args: ('用户创建对象参数2',)
    kwargs: {'Meta_call_kwarg': None, 'class_decorator_new_kwargs': None}
ic| 'Class.__init__ 后'
ic| 'Meta.__call__ 后': 'Meta.__call__ 后'
    type(tmp): <class '__main__.Cls'>
    tmp: <__main__.Cls object at 0x000002519F8FEB20>
ic| 'class_decorator_new 后': 'class_decorator_new 后'
    type(obj): <class '__main__.Cls'>
```



### 测试用例

```py
```



### Python单例实现1

* 实现要点
  * 在父类`Class.__new__`中
  * 对象创建前
  * 判断对象是否已经创建

```py
class Singleton(object):
    """通用单例父类

    实现__new__方法
	并在将一个类的实例绑定到类变量_instance上,
    如果cls._instance为None说明该类还没有实例化过,实例化该类,并返回
    如果cls._instance不为None,直接返回cls._instance
    """

    def __new__(cls, *args, **kw):
        if not hasattr(cls, '_instance'):
            
            # 调用父类的构造函数，以确保正确地初始化对象
            orig = super(Singleton, cls)
            
            # 注意参数args、kw不传会报错，虽然没有实际用处
            cls._instance = orig.__new__(cls, *args, **kw)
            
            # cls._instance = super(Singleton, cls).__new__(cls, *args, **kw)
            # cls._instance = object.__new__(cls, *args, **kw)

        return cls._instance


# 使用单例
class MySingleton(Singleton):
    a = 1

s1 = MySingleton()
s2 = MySingleton()


# 测试单例
s1.a = 3
s2.a # 也等于3

id(s1) == id(s2) # True
s1 == s2 # True
s1 is s2 # True

```



### Python单例实现2

* 父类`Class.__new__`中
* 对象创建后
* 用旧对象的所有属性覆盖新对象的所有属性

```py
class Borg(object):
    '''
    所谓单例就是所有引用(实例、对象)拥有相同的状态(属性)和行为(方法)
   	同一个类的所有实例天然拥有相同的行为(方法)
    只需要保证同一个类的所有实例具有相同的状态(属性)即可
    所有实例共享属性的最简单最直接的方法就是__dict__属性指向(引用)同一个字典(dict)
    '''
    
    _state = {}
    
    def __new__(cls, *args, **kw):
        ob = super(Borg, cls).__new__(cls, *args, **kw)
        ob.__dict__ = cls._state
        return ob


# 使用单例
class MyBorg(Borg):
    a = 1


b1 = MyBorg()
b2 = MyBorg()


# 测试单例
b1.a = 3
b2.a # 3

id(b1) == id(b2) # False
b1 == b2 # False
b1 is b2 # False
b1.__dict__ == b2.__dict__ # True

```



### Python单例实现3

* 元类`Meta.__call__`中
* 类创建后，对象创建前
* 判断对象是否已经创建

```py
# 方法3:本质上是方法1的升级（或者说高级）版
# 使用__metaclass__（元类）的高级python用法
class Singleton(type):
    # 元类初始化
    def __init__(cls, name, bases, dict):
        super(Singleton, cls).__init__(name, bases, dict)
        cls._instance = None
    
    # 元类实例化（类创建）
    def __call__(cls, *args, **kw):
        if cls._instance is None:
            cls._instance = super(Singleton, cls).__call__(*args, **kw)
        return cls._instance


class MySingleton(object):
    __metaclass__ = Singleton

s1 = MySingleton()
s2 = MySingleton()

s1.a = 3
s2.a # 3
id(s1) == id(s2) # True
s1 == s2 # True
s1 is s2 # True
```



### Python单例实现4

* 使用类装饰器，每次创建对象前
* 对象创建前
* 判断对象是否已经创建
* 实例保存在装饰器闭包中

```py
# 方法4:也是方法1的升级（高级）版本,
# 使用装饰器(decorator),
# 这是一种更pythonic,更elegant的方法,
# 单例类本身根本不知道自己是单例的,因为他本身(自己的代码)并不是单例的

def singleton(cls, *args, **kw):
    instances = {}
    
    def _singleton():
        if cls not in instances:
            instances[cls] = cls(*args, **kw)
        return instances[cls]
    
    return _singleton


@singleton # 装饰class的__new__
class AnyClass(object):
    a = 1
    
    def __init__(self, x=0)
        self.x = x
```



## 创建类 - 工厂模式

* 分类：
    * 简单工厂模式：又称静态工厂方法模式。通常使用静态类方法或者函数实现。
    * 工厂方法模式：父类Factory，子类覆盖方法实现工厂。
    * 抽象工厂模式：生产的对象是一个产品族，每个产品族产生一个工厂父类。



## 创建类 - 简单工厂模式

* 简单工厂模式
  * Simple Factory Pattern
  * 也叫做静态工厂方法模式



* 什么是简单工厂模式
    * 专门定义一个类来负责创建其他类的实例，根据参数的不同创建不同类的实例
    * 被创建的实例通常具有共同的父类
    * 或者说，不直接向客户端暴露对象创建的实现细节，而是通过一个工厂类来负责创建产品类的实例



* 简单工厂模式中的角色
  * 工厂，Creator
  * 抽象产品，Product
    * 使产品对外有相同抽象接口，可以对外统一使用方式
  * 具体产品，Concrete Product



* 优点
  * 隐藏了对象创建的实现细节
  * 客户端不需要修改代码



* 缺点
  * 违反了单一职责原则，将创建逻辑集中到一个工厂类里
  * 当添加新产品时，需要修改工厂类代码，违反了开闭原则



* 示例

```py
# 抽象产品
class Animal:
    pass


# 具体产品
class Cat(Animal):
    pass

class Dog(Animal):
    pass


# 工厂
class AnimalShelter:

    def adopt_a_pet(kind_of_pet)
        if kind_of_pet = 'cat':
            return Cat()
        elif kind_of_pet = 'dog':
            return Dog()
        else:
            raise TypeError('Unknown kind of pet')
```



* 示例

```py
# 抽象产品
class ProductOpt:
    def get_result(self):
        pass

    
# 具体产品
class ProductAdd(ProductOpt):
    def get_result(self):
        return self.num1 - self.num2

class ProductSub(ProductOpt):
    def get_result(self):
        return self.num1 - self.num2
    
class ProductErr(ProductOpt):
    def get_result(self)
        print("error")
        return 0


# 工厂
class Factory:
    operation = {}
    operation['+'] = ProductAdd()
    operation['-'] = ProductSub()
    
    def create_product(self, ch):
        if ch in self.operation:
            op = self.operation[ch]
        else:
            op = ProductErr()
        return op


# 使用工厂
factory = Factory()
product = factory.create_product('+')
product.num1 = 1
product.num2 = 2
product.get_result() # 3
```



## 创建类 - 工厂方法模式
* 什么是工厂方法模式
    * 定义一个用于创建对象的接口，即抽象工厂，每种产品实现自己的具体工厂，使用时让客户端决定实例化哪个类



* 角色
  * 抽象工厂，Creator
  * 具体工厂，Concrete Creator
  * 抽象产品，Product
  * 具体产品，Concrete Product



* 优点
  * 每个具体产品都对应一个具体工厂，不需要修改工厂代码
  * 隐藏了对象创建的实现细节



* 缺点
  * 每增加一个具体的产品类，就必须增加一个相应的具体工厂类
  * 只适用于，创建的过程特别复杂时



* 示例

```py
# 抽象产品
class Animal(metaclass=ABCMeta):
    pass


# 具体产品
class Cat(Animal):
    pass

class Dog(Animal):
    pass


# 抽象工厂
class AdoptAnimal(metaclass=ABCMeta):
    @abstractmethod
    def adopt(self):
        pass
    

# 具体工厂
class AdoptCat(AdoptAnimal):
    def adopt(self):
        return Cat()


class AdoptDog(AdoptAnimal):
    def adopt(self):
        return Dog()


# 工厂
class AnimalShelter:
    def adopt_a_pet(clsAdoptAnimal)
        pet = clsAdoptAnimal().adopt()


# 使用工厂
pet = AnimalShelter().adopt_a_pet(AdoptCat)
```



## 创建类 - 抽象工厂模式

* 什么是抽象工厂模式
  * 定义一个工厂类接口，让工厂子类来创建一系列相关或相互依赖的对象
  * 提供一个创建一系列相关或相互依赖的对象的接口，而无须指定他们的具体类



* 对比工厂方法模式
  * 抽象工厂模式中的每个具体工厂都生产一套产品



* 优点
  * 将客户端与类的具体实现相分离
  * 每个工厂创建了一个完整的产品系列，易于交换产品系列
  * 有利于产品的一致性（产品之间的约束关系）



* 缺点
  * 难以支持新的种类的（抽象）组件



* 示例
  * 生产一部电脑，需要三个部分，主机、操作系统软件、显示器，三类组件对象
  * 每类组件都有不同的子类
    * 主机
      * 联想
      * 戴尔
      * 小米
    * 显示器
      * 三星
      * AOC
    * 操作系统
      * Linux
      * Windows
  * 每个生产电脑的具体工厂，分别生产一部电脑所需要的三个组件对象

```py
# 一系列抽象组件
class OS(metaclass=ABCMeta):
    @abstractmethod
    def name(self):
        pass


class Host(metaclass=ABCMeta):
    @abstractmethod
    def name(self):
        pass


class Display(metaclass=ABCMeta):
    @abstractmethod
    def name(self):
        pass
    


# 一系列具体组件
class Windows(OS):
    def name(self):
        ic('Windows')


class Linux(OS):
    def name(self):
        ic('Linux')


class HP(Host):
    def name(self):
        ic('HP')


class Dell(Host):
    def name(self):
        ic('Dell')


class Sumsang(Display):
    def name(self):
        ic('Sumsang')

    
class AOC(Display):
    def name(self):
        ic('AOC')

        

# 产品
class Computer:
    def __init__(self, os_cls, host_cls, display_cls):
        self._os_cls = os_cls
        self._host_cls = host_cls
        self._display_cls = display_cls

    def name(self)
        self._os_cls().name()
        self._host_cls().name()
        self._display_cls().name()



# 抽象工厂
class Factory(metaclass=ABCMeta):
    @abstractmethod
    def make_os(self):
        pass
    
    @abstractmethod
    def make_host(self):
        pass

    @abstractmethod
    def make_display(self):
        pass

	def make_computer(self):
        computer = Computer(self.make_os(), self.make_host(), self.make_display())
        return computer
    

# 具体工厂
class Factory1(Factory)
	def make_os(self):
        return Windows
    
    def make_host(self):
        return HP

    def make_display(self):
        return Sumsang


class Factory2(Factory)
	def make_os(self):
        return Linux
    
    def make_host(self):
        return Dell

    def make_display(self):
        return AOC



# 使用工厂
factory = Factory1()
computer = factory.make_computer()
computer.name()   


```



## 创建类 - 建造者模式

* 也叫做
  * 构建模式
  * 生成（器）模式



* 定义
    * 将一复杂对象的构建过程和它的表现分离，使得同样的构建过程可以创建不同的表现
    * 构建拆分为
      * 指挥者 Director 负责控制构建顺序
      * 具体建造者 Concrete Builder 负责控制构建元素的种类



* 对比抽象工厂模式
  * 抽象工厂模式侧重于多个系列的产品对象
  * 建造者模式侧重于构建的过程
  * 建造者模式进一步将构建过程从抽象工厂中拆分出来



* 优点
    * 隐藏了一个产品的内部结构和装配过程
    * 将构造代码与表示代码分开
    * 可以对构造过程进行更精细的控制



* 缺点
    * 无



* 角色：
    * 产品，Product
    * 抽象建造者，Builder，可以简化进Director作为一个函数
    * 具体建造者，Concrete Builder
    * 指挥者，Director，BuilderManager



## 创建类 - 原型模式

* 也叫做
  * 克隆模式



* 定义
    * 通过复制原型对象创建新对象，而非用类创建对象。



* 使用场景
    * 对象在修改过之后，需要复制多份的场景
    * 需要优化资源的情况（浅拷贝）
    * 构建类时重复性的复杂工作不需要再多次进行，直接复制。



* 优点
    * 性能好，避免类构建，属性构建，节省资源（浅拷贝）。
    * 简化对象创建。



* 缺点
    * 绕过了类创建过程，需要注意引起bug。
    * 需要注意某些编程语言中对静态变量，静态函数的影响。



* 示例1

```py
"""
类似Photoshop的平面设计软件的图层概念，使用图层创建图层，修改应用在各个图层上。
每次重新创建图层没有必要，只需复制一份资源即可。
"""

import copy

class GraphLayer(object):
    def __init__(self):
        self.background = ''
        self.foreground = ''
    
    def clone(self):
        return copy.copy(self)
    
    def deep_clone(self):
        return copy.deepcopy(self)

l1 = GraphLayer()
l1.background = 'black'
l1.foreground = 'red'

l2 = l1.clone()
l3 = l1.deep_clone()
```



* 示例2

```py
# 原型与工厂模式的区别应该是少一个与与产品平行的工厂类，通过克隆自己，可以创造多个对象

# 有一个哺乳动物的原型，每个动物有名称，
# 人有很多，所以有很多Object,我们通过clone得到人的对象，然后在附上不同属性
# 猴子也有很多，我们也可以通过clone得到多个猴子


class ProtoType(object):
    typename = 'mammalian'
    
    def __init__(self):
        pass
    
    def clone(self):
        pass

class Person(ProtoType):
    def __init__(self):
        self.hair = 'black'
        self.name = 'person'
        ProtoType.__init__(self)
    
    def clone(self):
        return Person()

class Monkey(ProtoType):
    def __init__(self):
        self.hair = 'red'
        self.Name = 'monkey'
        super(ProtoType, self).__init__()
    
    def clone(self):
        return monkey()

p = Person()
p1 = p.clone()
p2 = p.clone()

m = Monkey()
m1 = m.clone()
m2 = m.clone()
```



* 抽象1

```py
from copy import copy, deepcopy

class Clone:
    def clone(self):
        return copy(self)
    
    def deep_clone(self):
        return deepcopy(self)

```



## 结构类 - 代理模式


* 定义
    * 为某对象，或者某类型提供一个代理，以控制对对象的访问。




* 应用场景
    * 对某特定对象进行功能和增强型扩展。如IP防火墙，远程访问代理。
    * 对对象进行保护。如大流量代理，安全代理。
    * 减轻对象负载。如权限代理。



* 三种应用场景

  * 远程代理，为远程的对象提供代理

  * 虚代理，根据需要创建很大的对象，例如延迟加载、延迟读取

  * 保护代理，控制对原始对象的访问，用于对象有不同访问权限时




* 优点
    * 职责清晰。符合单一职责原则，实际业务和权限控制相分离。
    * 扩展性强。保护对象改变不影响代理对外接口。
    * 保护对象处理逻辑。使用代理检查参数，保证对象输入参数。




* 缺点
    * 可能会降低整体业务的处理效率和速度。




* 角色：
    * 主题，Subject
    * 真实主题，RealSubject
    * 代理主题，ProxySubject



* 使用要点

  * 尽量代理抽象类，更加通用

  * 实际上将代理功能和实际功能分开，可以更加符合单一职责原则。



* 示例

```py
from abc import ABC, abstractmethod

class AbstractSubject(ABC):

    @abstractmethod
    def request(self):
        pass

class Subject(AbstractSubject):
    def request(self):
        print('Doing something.')

# 也可以继承一个新的Proxy虚基类
class Proxy(AbstractSubject):
    def __init__(self, subject):
        self._subject = subject

    def request(self, ip):
        if ip == 'passwd' :
            self._subject.request()
        else:
            print('Permission denied.')

subject = Subject()
proxy = Proxy(subject)
proxy.request('passwd')
proxy.request('error')
```



## 结构类 - 装饰模式

* 也叫做
  * 装饰器模式



* 简而言之
    * 装饰器




* 说明
    * 装饰模式是代理模式的一个特例
    * 装饰模式是继承的一种替代模式



* 定义
    * 动态地给一个对象增加一些额外的职责，就拓展对象功能来说，装饰模式比生成子类的方式更为灵活



* 应用场景
    * 需要扩展、增强或者减弱一个类的功能



* 优点
    1. 是继承的一个替代方案（组合），可以轻量级地扩展被装饰对象的功能。
    2. AOP(Aspect Oriented Programing)面向切面编程，提取多种类中的类似行为形成抽象。



* 缺点
    * 多层装饰器调试、维护比较困难



* 示例

```py
'''
饮料加冰，饮料加糖
'''

class Beverage: # 饮品类
    def __init__(self):
        self._name = ''
        self._price = 0.0

    @property
    def price(self):
        return self._price
        
    @property
    def name(self):
        return self._price

class Coke(Beverage):
    def __init__(self):
        self._name = 'coke'
        self._price = 4.0
        
class Milk(Beverage):
    def __init__(self):
        self._name = 'milk'
        self._price = 5.0

class BeverageDecorator:
# class BeverageDecorator(Beverage): # 装饰之后仍然是Beverage
    def __init__(self, beverage)
        self._beverage = beverage
    @property
    def name(self): pass
    @property
    def price(self): pass

class IceDecorator(BeverageDecorator):
    @property
    def name(self):
        return self._beverage.name + '+ice'
    @property
    def price(self):
        return self._beverage.price + 0.3

class SugarDecorator(BeverageDecorator):
    @property
    def name(self):
        return self._beverage.name + '+sugar'
    @property
    def price(self):
        return self._beverage.price + 0.5

coke = Coke()
coke_ice = IceDecorator(coke)
coke_sugar = SugarDecorator(coke)
```



## 结构类 - 适配模式

* 也称作
  * 适配器模式
  * 变压器模式
  * 包装模式



* 定义：
    * 将一个类的接口转换成客户端期待的另一种接口，从而使原本接口不匹配的类能够一起工作。
    * 简而言之，接口转换



* 与装饰模式的区别
  * 装饰模式是给一个对象增加了一些额外的职责，而适配器模式是将另一个对象进行了伪装。



* 应用场景
    * 不修改现有接口，使接口兼容新场景业务
    * 兼容数据库接口
    * 兼容数据读取硬件接口



* 角色
  * 目标接口，Target
  * 待适配的类，Adaptee
  * 适配器，Adapter



* 优点
    * 可以让两个接口不同的类一起运行。
    * 提高了类的复用度，经过“伪装”的类充当新角色。
    * 适配器可以灵活拆卸



* 缺点
    * 复杂度提高，效率下降，从新设计系统时不应该使用。



* 示例
  * 台灯需要2相插座
  * 实际只有三项插座

```py
class Socket3:
    def __init__(self):
        self._live_wire = '1'
        self._neutral_wire = '1'
        self._earch_wire = '1'
    
    def connect3(self):
        return  (self._live_wire, self._neutral_wire, self._earch_wire)


class Socket2:
    def __init__(self):
        self._live_wire = '1'
        self._neutral_wire = '1'

    def connect2(self):
        return  (self._live_wire, self._neutral_wire)

class Lamp:
    def connect(socket):
        if isinstance(socket, Socket2):
            socket.connect2()
        else:
            raise TypeError

```

* 实现方式一，类适配器

```py
# 类适配器
class Adapter(Socket2, Socket3):
    def connect2(self):
        socket = Socket3.connect3()
        return (socket._live_wire, self._neutral_wire)

l = Lamp()
l.connect(Adapter())
```

* 实现方式二，对象适配器

```py
# 对象适配器
class Adapter(Socket2):
    def __init__(self, socket)
        self._sock3 = socket
    
    def connect2(self):
        return (self._sock3._live_wire, self_neutral_wire)

l = Lamp()
l.connect(Adapter(Socket3()))
```



## 结构类 - 外观模式

* 也叫做
    * 门面模式




* 概念
    * 要求一个子系统的外部与其内部的通信必须通过一个统一的对象进行。
    * 门面模式提供一个高层次的接口，使得子系统更易于使用。
    * 门面模式注重“统一的对象”，也就是提供一个访问子系统的接口。



* 门面模式与模板模式的区别
    * 门面模式与模板模式有类似的地方，都是对一些需要重复方法的封装。但从本质上来说，是不同的。
    * 模板模式是对类本身的方法的封装，其被封装的方法也可以单独使用；
    * 门面模式，是对子系统的封装，其被封装的接口理论上是不会被单独提出来用的。



* 使用场景
    * 为一个复杂的子系统提供一个外界访问的接口。一般用于界面交互。
    * 需要简化操作界面时。如常见的扁平化系统操作界面。



* 优点
    * 减少系统间相互依赖，提高了系统的灵活性
    * 提高了整体系统的安全性，封装对外接口，隐藏内部细节



* 缺点
    * 不符合开闭原则，一旦系统成型后需要修改，几乎只能重写门面代码，这比继承或者复写等方式，或者其他一些符合开闭原则的模式风险更大。



* 角色
    * 外观，Facade
    * 子系统类，SubSystem classes



* 示例

```py
class AlarmSensor:
    def run(self):
        print('Alarm Ring...')

class WaterSprinker:
    def run(self):
        print('Spray Water...')

class EmergencyDialer:
    def run(self):
        print('Dial 119...')


# 无门面
alarm_sensor = AlarmSensor()
water_sprinker = WaterSprinker()
emergency_dialer = EmergencyDialer()
alarm_sensor.run()
water_sprinker.run()
emergency_dialer.run()


# Facade门面类
class EmergencyFacade:
    def __init__(self):
        self.alarm_sensor = AlarmSensor()
        self.water_sprinker = WaterSprinker()
        self.emergency_dialer = EmergencyDialer()
    
    def run(self):
        self.alarm_sensor.run()
        self.water_sprinker.run()
        self.emergency_dialer.run()


emergency_facade = EmergencyFacade()
emergency_facade.run()
```



## 结构类 - 组合模式

* 也叫做
  * 部分整体模式



* 定义
    * 将对象组合成树形结构以表示“部分”和“整体”的层次结构，使得用户对单个对象和组合对象的使用具有一致性



* 简而言之
  * DOM，对象文档模型，所有类型的元素都是节点



* 使用场景
    * 维护部分和整体的逻辑关系，凡是树形结构都可以使用组合模式。
    * 文件目录
    * 部门组织架构
    * DOM树



* 角色
  * 抽象组件，Component
  * 叶子组件，Leaf
  * 复合组件，Composite
  * 客户端，Client



* 优点
    * 节点增加减少非常自由方便。这是树形结构的特点。
    * 使用节点非常方便。



* 缺点：
    * 叶子节点和分支节点直接使用了实现类，从而不方便使用抽象类，限制了接口的影响范围。



* 示例
  * 组装电脑

```py
from abc import ABCMeta, abstractmethod

class ComputerComponent(metaclass=ABCMeta):
    def __init__(self, name):
        self._name = name
    
    def show_info(self, indent = ''):
        print(indent, self._name)


class CPU(ComputerComponent):
    pass


class MemoryCard(ComputerComponent):
    pass


class HardDisk(ComputerComponent):
    pass


class GraphicsCard(ComputerComponent):
    pass


class Battery(ComputerComponent):
    pass


class Fan(ComputerComponent):
    pass


class Displayer(ComputerComponent):
    pass


class ComputerComposite(ComputerComponent):
    def __init__(self, name):
        super().__init__(name)
        self._components = []

    def show_info(self, indent):
        super().show_info(indent)
        print(indent, "子部件:")
        indent += '\t'
        for e in self._components:
            e.show_info(indent)

    def add_component(self, component):
        self._components.append(component)

    def rmv_component(self, component):
        self._components.remove(component)


class Mainboard(ComputerComposite):
    pass


class ComputerCase(ComputerComposite):
    pass


class Computer(ComputerComposite):
    pass


def test():
    main_board = Mainboard('Mainboard')
    main_board.add_component(CPU('CPU'))
    main_board.add_component(MemoryCard('MemoryCard'))
    main_board.add_component(HardDisk('HardDisk'))
    main_board.add_component(GraphicsCard('GraphicsCard'))

    computer_case = ComputerCase('ComputerCase')
    computer_case.add_component(main_board)
    computer_case.add_component(Battery('Battery'))
    computer_case.add_component(Fan('Fan'))

    computer = Computer('Coumputer')
    computer.add_component(computer_case)
    computer.add_component(Displayer('Displayer'))

    computer.show_info('')

if __name__ == '__main__':
    test()
```



## 结构类 - 享元模式，flyweight

* 定义
    * 使用共享对象支持大量细粒度对象。大量细粒度的对象的支持共享，可能会涉及这些对象的两类信息：内部状态信息和外部状态信息。内部状态信息就是可共享出来的信息，它们存储在享元对象内部，不会随着特定环境的改变而改变；外部状态信息就不可共享的信息了。享元模式中只包含内部状态信息，而不应该包含外部状态信息。这点在设计业务架构时，应该有所考虑。



* 使用场景
    * 进程池、线程池、连接池等申请资源较多时。
    * 大型系统中，类似对象较多时。



* 优点
    * 减少重复对象
    * 节约系统资源



* 缺点
    * 虽然节约了系统资源，但同时也提高了系统的复杂性。要区分好内部状态外部状态。
    * 并发系统下会产生线程安全问题。



* 示例

```py


```



## 结构类 - 桥模式

* 也叫做

  * 桥梁模式

  * 桥接模式



* 定义
    * 将抽象与实现解耦（注意此处的抽象和实现，并非抽象类和实现类的那种关系，而是一种角色的关系，这里需要好好区分一下），可以使其独立变化。
    * 下例中，Pen只负责画，但没有形状，它终究是不知道要画什么的，所以我们把它叫做抽象化角色；而Shape是具体的形状，我们把它叫做实现化角色。抽象化角色和实现化角色是解耦的。
    * 所谓的桥，就是抽象化角色的抽象类和实现化角色的抽象类之间的引用关系。



* 简而言之
  * 代码实现的进一步抽象、解耦
  * 将一个事物的两个维度分离，使其都可以独立地变化



* 应用场景
    * 不适合用继承或者原继承关系中抽象类可能频繁变动的情况，可以将原类进行拆分，拆成实现角色和抽象化角色。
    * 重用性比较大的场景。如开关控制逻辑，开关抽象，具体开关操作多种。



* 角色
  * 抽象，Abstraction
  * 细化抽象，RefinedAbstraction
  * 实现者，Implementor
  * 具体实现者，ConcreteImplementor



* 优点
    * 抽象角色与实现角色相分离，二者可以独立设计，不受约束。
    * 扩展性强，抽象角色和实现角色可以灵活扩展



* 缺点
    * 增加系统设计复杂度。
    * 增加对系统的理解难度。



* 示例

```py
# 画笔与形状分离
class Shape:
    def __init__(self, *args):
        self.name = ''
        self.param = ''

class Pen:
    def __init__(self, shape)
        self.shape = shape
        self.type = ''
    
    def draw(self): pass

class Rectangle(Shape):
    def __init__(self, height, width):
        self.name = 'Rectangle'
        self.param = 'height %s width %s' % (height, width)
        print

```



## 行为类 - 策略模式

* 定义
    * 定义一系列算法，将每个算法都封装起来，并且使它们之间可以相互替换。策 略模式使算法可以独立于使用它的用户而变化



* 角色
  * 抽象策略，Strategy
  * 具体策略，ConcreteStrategy
  * 上下文，Context



* 应用场景
    * 算法策略比较经常地需要被替换时，可以使用策略模式。如现在超市前台，会常遇到刷卡、某宝支付、某信支付等方式，就可以参考策略模式



* 优点
    * 各个策略可以自由切换，这也是依赖抽象类设计接口的好处之一
    * 减少代码冗余
    * 扩展性优秀，移植方便，使用灵活



* 缺点
    * 项目比较庞大时，策略可能比较多，不便于维护
    * 策略的使用方必须知道有哪些策略，才能决定使用哪一个策略，这与迪米特法则相违背



* 示例

```py
# 条条大路通罗马


```



## 行为类 - 责任链模式

* 也叫做
  * 职责链模式
  * 职责模式



* 定义
    * 使多个对象都有机会处理请求，从而避免了请求的发送者和接收者之间的耦合关系。将这些对象连成一条链，并沿着这条链传递该请求，直到有对象处理它为止。



* 速记
  * DOM事件传播



* 应用场景
    * 一个请求可能由一个对请求有链式优先级的处理群所处理时，可以考虑责任链模式



* 优点
    * 将请求者与处理者分离，请求者并不知道请求是被哪个处理者所处理，易于扩展



* 缺点
    * 如果责任链比较长，会有比较大的性能问题
    * 业务处理异常会难以定位是哪个处理者的问题



* 抽象
  * 抽象处理者，Handler
  * 具体处理者，ConcreteHandler
  * 客户端，Client



* 示例：批假系统

```py
# 各个层级主管批假权限不同
# LineManager <3
# DepartmentManager <3  >7
# GeneralManager >7

class Manager:
    def __init__(self, successor):
        self._successor = successor
    
    def handle_request(self, request): pass


class LineManager(Manager):
    def handle_request(self, dayoff):
        if dayoff <= 3:
            return True
        else:
            return self.handle_request(dayoff)

class DepartmentManager(Manager):
    def handle_request(self, dayoff):
        if dayoff <= 7:
            return True
        else:
            return self.handle_request(dayoff)

class GeneralManager(Manager):
    def handle_request(self, dayoff):
        if dayoff < 14:
            return True
        else:
            return False

gm = GeneralManager(None)
dm = DepartmentManager(gm)
lm = LineManager(dm)

lm.handleRequest(3)
lm.handleRequest(5)
lm.handleRequest(10)
lm.handleRequest(15)
```



## 行为类 - 命令模式

* 定义：
    * 将一个请求封装成一个对象，从而可以使用不同的请求将客户端参数化，对请求排队或者记录请求日志，可以提供命令的撤销和恢复功能。
* 使用场景：
    * 触发-反馈机制的系统都可以使用命令模式思想。如基于管道结构的命令系统shell，GUI系统中的操作反馈（点击、键入）
* 优点：
    * 低耦合，调用者和接收者之间没有直接关系，二者通过命令中的execute接口联系。
    * 扩展性好，新命令容易加入，也很容易拼出组合命令。
* 缺点：
    * 命令较多时，命令类和命令对象数量也会增加，系统膨胀严重。
* 对象：
    * 接收者，Receiver
    * 命令，Command
    * 调度者，Invoker 
    * 用户，Client



## 行为类 - 中介模式

* 也叫做
  * 中介者模式
  * 调停模式



* 定义
    * 用一个中介对象来封装一系列的对象交互，中介者使各对象不需要显示地相互引用，从而使其耦合松散，而且可以独立地改变他们之间的交互。



* 应用场景
    * 一组对象以定义良好但复杂的方式进行通信。产生的相互依赖关系结构混乱且难以理解。
    * 一个对象引用其他很多对象并且直接与这些对象通信，导致难以复用该对象。
    * 想通过一个中间类来封装多个类中的行为，同时又不想生成太多子类。



* 优点
    * Mediator将原本分布于多个对象间的行为集中在一起，作为一个独立的概念将其封装在一个对象中，简化了对象之间的交互。
    * 将多个调用者与多个实现者之间的多对多的交互关系，转换为一对多的交互关系，一对多的交互关系更易于理解，维护和扩展，大大减少了多个对象之间相互交叉引用的情况。



* 缺点
    * 中介者承接了所有的交互逻辑，交互的复杂度转变成了中介者的复杂度，中介者类会变得越来越庞大和复杂，以至于难以维护。
    * 中介者出问题会导致多个使用者同时出问题。



* 示例
    * 多对多通信，封装成一个总线。
    * 文件系统，封装文件系统类型，抽象文件读写。
    * 设备管理器，封装设备选择，设备使用者与设备管理器交互。



## 行为类 - 模板模式

* 也叫做
  * 模板方法模式



* 简而言之
  * 父类实现，子类继承



* 定义
    * 定义一个操作中的算法的框架，而将算法中用到的某些具体的步骤放到子类中实现，使得子类可以在不改变算法结构的情况下重新定义该算法的某些特定步骤。这个定义算法骨架的方法就叫模板方法模式，简称模板模式。



* 应用场景
    * 对一些复杂的算法进行分割，将其算法中固定不变的部分设计为模板方法和父类具体方法，而一些可以改变的细节由其子类来实现。即一次性实现一个算法的不变部分，并将可变的行为留给子类实现。
    * 各子类中公共的行为应被提取出来并集中到一个公共父类中以避免代码重复。
    * 需要通过子类来决定父类算法中某个步骤是否执行，实现子类对父类的反向控制。



## 行为类 - 迭代器模式

* 也叫做
  * 迭代模式



* 简而言之
  * 迭代器



* 使用场景
  * 在python中，迭代器并不用举太多的例子，因为python中的迭代器应用实在太多了（不管是python还是其它很多的编程语言中，实际上迭代器都已经纳入到了常用的库或者包中）。而且在当前，也几乎没有人专门去开发一个迭代器，而是直接去使用list、string、set、dict等python可迭代对象，或者直接使用__iter__和next函数来实现迭代器。



## 行为类 - 访问模式

* 也叫做
    * 访问者模式




* 简而言之
    * 数据结构与算法解耦
    * sorted、reversed




* 定义
    * 封装一些作用于某种数据结构中各元素的操作，它可以在不改变数据结构的前提下定义作用于这些元素的新的操作



* 优点
    * 数据和操作（算法）分离，降低了耦合度。将有关元素对象的访问行为集中到一个访问者对象中，而不是分散在一个个的元素类中，类的职责更加清晰。
    * 添加新的访问操作很方便。使用访问模式，增加新的访问操作就意味着增加一个新的具体方法类，实现简单，无需修改源代码，符合“开闭原则”。
    * 让用户能够在不修改现有元素层次结构的情况下，定义作用于该层次结构的操作。



* 缺点
    * 增加新的元素类很困难。违背了开闭原则
    * 破坏数据对象的封装性



* 角色
    * 访问者，Visitor，算法
    * 数据结构，DataNode
    * 对象结构，ObjectStructure，DataNode容器，可遍历



## 行为类 - 发布订阅模式

* 也叫做
  * 观察者模式
  * 监听模式
  * 模型视图模式
  * 源监听模式
  * 从属者模式



* 定义
    * 定义对象间一种一对多的依赖关系，当该对象状态改变时，所有依赖于它的对象都会得到通知并被自动更新



* 使用场景
    * 消息交换场景
      * 消息队列
    * 多级触发场景
      * 响应中断，发消息给所有处理者



* 优点
    * 观察者与被观察者之间是抽象耦合的。
    * 可以将许多符合单一职责原则的模块进行触发，可以方便地实现广播



* 缺点
    * 可能带来整体系统效率的浪费
    * 如果被观察者之间有依赖关系，梳理逻辑关系比较麻烦。



* 实现角色
    * 抽象主题，Subject
    * 具体主题，ConcreteSubject，发布者
    * 抽象观察者，Observer
    * 具体观察者，ConcreteObserver，订阅者



* 业务角色
    * 观察者模式
      * 观察者，Observer
      * 被观察者，Observable
    * 观察者模式
      * 观察者，Observer
      * 被观察主题，Subject
    * 发布订阅模式
      * 发布者，Publish
      * 订阅者，Subscribe
    * 模型视图模式
      * 模型，Model
      * 视图，View
    * 源监听模式
      * 源，Source
      * 监听者，Listener
    * 从属者模式
      * 被从属者
      * 从属者，Dependents



* 分类：
    * 推模型：只获取被观察者发送的信息
    * 拉模型：获取被观察者对象，观察者自行拉取所需信息



* 示例1

```py
# 火警触发警报、灭火器、急救中心

class Observer:
    def observe(self): pass

class AlarmSensor(Observer):
    def observe(self):
        print('Alarm Sensor observe')

class WaterSprinker(Observer):
    def observe(self):
        print('Water Sprinker observe')
    
class EmergencyDialer(Observer):
    def observe(self):
        print('Emergency Dialer observe')

class Observed:
    def __init__(self):
        self._observers = []
        
    def add_observer(self, o):
        self.self._observers.append(o)
        
    def notify_all(self):
        for o in self._observers:
            o.observe()

a = AlarmSensor()
w = WaterSprinker()
e = EmergencyDialer()

o = Observed()
o.add_observer(a)
o.add_observer(w)
o.add_observer(e)
o.notify_all()
```

* 抽象示例

```py
from abc import ABCMeta, abstractmethod

class Observer(metaclass=ABCMeta):
    @abstractmethod
    def update(self, observable, object): pass

class Observable:
    def __init__(self):
        self.__observers = []
    
    def add_observer(self, observer):
        self.__observers.append(observer)
    
    def remove_observer(self, observer):
        self.__observers.remove(observer)
    
    def notify_observers(self, object=0):
        for o in self.__observers:
            o.update(self, object)

class WaterHeater(Observable):
    def __init__(self):
        super().__init__()
        self.__temperature = 25
    
    def get_temperature(self):
        return self.__temperature
    
    def set_temperature(self, temperature):
        self.__temperature = temperature
        print("当前温度是" + str(self.__temperature))
        self.notify_observers()

class WashingMode(Observer):
    def update(self, observable, object):
        if isinstance(observable, WaterHeater):
            tmp = observable.get_temperature()
            if tmp >= 50 and tmp < 70:
                print('洗澡温度')

class DrinkingMode(Observer):
    def update(self, observable, object):
        if isinstance(observable, WaterHeater):
            if observable.get_temperature() >= 100:
                print('饮用水温度')

def test_water_heater():
    heater = WaterHeater()
    washing_obser = WashingMode()
    drinking_obser = DrinkingMode()
    heater.add_observer(washing_obser)
    heater.add_observer(drinking_obser)
    heater.set_temperature(40)
    heater.set_temperature(60)
    heater.set_temperature(100)
```



## 行为类 - 解释器模式

* 也叫做
  * 解释模式



* 定义
    * 给定一种语言，定义它的文法表示，并定义一个解释器，该解释器使用该表示来解释语言中的句子。
    * 一般需要定义终结符和非终结符。



* 使用场景
    * 一个问题重复发生，可以考虑使用解释器模式。在数据处理和日志处理过程中使用较多，当数据的需求方需要将数据纳为己用时，必须将数据“翻译”成本系统的数据格式。
    * 特定语法解释器。



* 优点
    * 在语法分析场景中，具有比较好的扩展性。规则修改和定制比较灵活。



* 缺点
    * 解释规则多样化会导致解析器的爆炸。
    * 解释器目标比较单一，行为规则比较固定，因而重要的模块中尽量不要使用解释器模式。



* 示例

```py
# 只能处理双值表达式
# 只支持单字符运算符
# 不能处理正负号
# 不能处理两位数

from abc import ABC, abstractmethod

class Expression(ABC):
    @abstractmethod
    def caculate(self): pass


class Var(Expression):
    def __init__(self, var):
        self._var = var

    def caculate(self):
        return float(self._var)


class DoubleValueOperator(Expression):
    S = ''
    
    def __init__(self, left, right):
        self._left = left
        self._right = right


class Add(DoubleValueOperator):
    S = '+'

    def caculate(self):
        return self._left.caculate() + self._right.caculate()


class Sub(DoubleValueOperator):
    S = '-'

    def caculate(self):
        return self._left.caculate() - self._right.caculate()


class Multi(DoubleValueOperator):
    S = '*'

    def caculate(self):
        return self._left.caculate() * self._right.caculate()


class Div(DoubleValueOperator):
    S = '/'

    def caculate(self):
        return self._left.caculate() / self._right.caculate()


class Power(DoubleValueOperator):
    S = '^'

    def caculate(self):
        return self._left.caculate() ** self._right.caculate()


def subclasses(cls):
    l = []
    for subcls in cls.__subclasses__():
        l.append(subcls)
        # 可能递归
        # subclasses(subcls)
    return l


def get_symbol_class_dict(cls):
    l = subclasses(cls)
    d = {}
    for i in l:
        d[i.S] = i
    return d


DVO_DICT = get_symbol_class_dict(DoubleValueOperator)


class Stack:
    def __init__(self):
        self._l = []

    def len(self):
        return len(self._l)

    def empty(self):
        return 0 == self.len()

    def push(self, item):
        self._l.append(item)

    def pop(self):
        return self._l.pop()

    def peek(self):
        if self.empty():
            return None
        else:
            self._l[self.len() - 1]

    def clear(self):
        self._l = []


class Calculator:
    def __init__(self):
        self._text = ''
        self._stack = Stack()
        self._tree = None

    def parse(self, text):
        self._stack.clear()
        left = right = None
        index = 0
        text = text.replace(' ', '')

        print(text)


        while(index < len(text)):
            c = text[index]
            
            if c in DVO_DICT:
                left = self._stack.pop()
                cls = DVO_DICT[c]
                index += 1
                right = Var(text[index])
                self._stack.push(cls(left, right))
            else:
                self._stack.push(Var(text[index]))
            index += 1
        self._tree = self._stack.pop()

    def caculate(self):
        return self._tree.caculate()


def test():
    c = Calculator()
    c.parse('1 + 2 + 3')
    print(c.caculate())

if '__main__' == __name__:
    test()
```



## 行为类 - 备忘录模式、备忘模式

* 定义
    * 在不破坏封装性的前提下，捕获一个对象的内部状态，并在该对象之外保存这个状态。这样就可以将该对象恢复到原来保存的状态。在备忘录模式中，如果要保存的状态多，可以创造一个备忘录管理者角色来管理备忘录



* 适用场景
    * 需要保存和恢复数据的相关状态场景
        * 游戏状态
        * 可能撤销
        * 事物回滚
    * 副本监控场景



* 优点
    * 提供了一种可以恢复状态的机制，使得用户能够比较方便地回到某个历史状态
    * 实现了信息封装，用户不需要关心状态的保存细节



* 缺点
    * 如果类成员变量过多会占用较多资源，每一次保存都会消耗一定内存



* 角色
    * 发起人，Originator，需要进行备份的对象
    * 备忘录，Memento，备份的状态。一个存档
    * 备忘录管理者，Caretaker，备份存档的管理者



* 抽象

```py
from copy import deepcopy

class Memento:
    def set_attr(self, dict):
        self.__dict__ = deepcopy(dict)
    
    def get_attr(self):
        return self.__dict__


class Caretaker:
    def __init__(self):
        self._mementos = {}
    
    def add_memento(self, name, memento):
        self._mementos[name] = memento
    
    def get_memento(self, name)
        return self._mementos[name]


class Originator:
    def create_memento(self):
        memento = Memento()
        memento.set_attr(self.__dict__)
        return memento
    
    def restore_from_memento(self, memento):
        self.__dict__.update(memento.get_attr()
```



## 行为类 - 状态模式、状态机

* 定义
    * 当一个对象内在状态改变时允许其行为改变，这个对象看起来像改变了类型



* 使用场景
    * 行为状态改变的场景。这点在各种控制器中非常常见。同时，逻辑结构为状态转移图的场景中都非常适用



* 优点
    * 状态模式的优点是结构清晰，相比于if else好理解
    * 封装性好，外部调用不必知道内部实现细节



* 缺点
    * 状态比较多时，子类会非常多，不便于管理




* 实现：各种资料实现方式有差异，有的侧重于封装状态，有的侧重于状态机
    * 封装状态的关键点在于，把状态迁移封装，但是任然有if..else..
        * 将状态迁移条件封装在状态子类，在新增状态的情况下无需修改原代码
    * 状态机的思想更加清晰，状态根据条件迁移
        * 有限状态机有成熟实现，需要已知状态
        * 无限状态机、可以自由添加状态，对扩展开放？能实现这种状态机的通用设计模式可能不存在。状态不可能与上下文解耦。



## 新设计模式-过滤器模式

* 比责任链模式简单，责任链模式有顺序关系，过滤器模式没有
* 循环迭代处理对象，比链式递进关系简单



## 新设计模式-对象池技术

* 比享元模式更进一步，通过借、还操作来复位对象状态。
* 可以通过sys.getrefcount()获得引用计数自动释放对象



* 抽象

```py
from abc import ABC, abstractmethod
import logging
import time
logging.basicConfig(level=logging.INFO)

class PooledObject:
    def __init__(self, obj):
        self.__obj = obj
        self.__busy = False
    
    def get_object(self):
        return self.__obj
    
    def set_object(self, obj):
        self.__obj = obj
    
    def busy(self):
        return self.__busy
    
    def set_busy(self, busy):
        self.__busy = busy

class ObjectPool(ABC):
    InitialNumOfObjects = 10
    MaxNumOfObjects = 50
    
    def __init__(self):
        self.__pools = []
        for i in range(0, ObjectPool.InitialNumOfObjects):
            obj = self.create_pooled_object()
            self.__pools.append(obj)
    
    @abstractmethod
    def create_pooled_object(self):
        pass
    
    def borrow(self):
        obj = self._find_free_object()
        if obj is not None:
            logging.info('借用')
        return obj
    
        if len(self.__pools) < ObjectPool.MaxNumOfObjects:
            pooled_obj = self.add_object()
            if pooled_obj is not None:
                pooled_obj.set_busy(True)
                logging.info('借用')
                return pooled_obj.get_object()
        
        return None
    
    def return(self, obj)
        for pooled_obj in self.__pools:
            if pooled_obj.get_object() == obj:
                pooled_obj.set_busy(False)
                logging.info('归还')
                break
    
    def add_object(self):
        obj = None
        if len(self.__pools) < ObjectPool.MaxNumOfObjects:
            obj = self.create_pooled_object()
            self.__pools.append(obj)
            logging.info('添加')
            return obj
    
    def clear(self):
        self.__pools.clear()
    
    def _find_free_object(self):
        obj = None
        for pooled_obj in self.__pools:
            if not pooled_obj.is_busy():
                obj = pooled_obj.get_object()
                pooled_obj.set_busy(True)
                break
        return obj
```



## 新设计模式-回调机制、函数式编程

* 回调是策略模式的一个特例



## 新设计模式-MVC、MVP、MVVM
