### this指针概念

> this指针的本质  是指针常量   指针的指向是不可修改的

我们知道在C++中成员变量和成员函数是分开存储的

每一个非静态成员函数只会诞生一份函数实例，也就是说多个同类型的对象会共用一块代码

那么问题是：这一块代码是如何区分那个对象调用自己的呢？

C++通过提供特殊的对象指针，this指针，解决上述问题。**this指针指向被调用的成员函数所属的对象**



this指针是隐含每一个非静态成员函数内的一种指针

this指针不需要定义，直接使用即可



this指针的用途：

- 当形参和成员变量同名时，可用this指针来区分

```c++
class per{
public:
  	int age;
    void func(int age){
        this->age = age;
    }
};
```



- 在类的非静态成员函数中**返回对象本身**，可使用return*this

```c++
class per{
public:
  	int age;
    
    per& func(per &p){
        this->age += p.age;
        return *this;
    }
    //上面的函数与下面的函数有一个区别，就是返回值的&
    //当有&时，则是返回对象本身
    //没有&时，则是返回对象副本
    per func(per &p){
        this->age += p.age;
        return *this;
    }
};
```

返回对象本身的机制可以实现**链式调用效果**
