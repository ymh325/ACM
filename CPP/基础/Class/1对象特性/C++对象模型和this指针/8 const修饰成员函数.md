### const修饰成员函数

常函数：

- 成员函数后加const后我们称为这个函数为**常函数**
- 常函数内不可以修改成员属性
- 成员属性声明时加关键字mutable后，在常函数中依然可以修改



常对象：

- 声明对象前加const称该对象为常对象
- 常对象只能调用常函数

```cpp
class per{
public:
  	int age;
    mutable h;
    
    //this的本质是一个指针常量（per* const this）,指向不可改变，但指向地址的值可以改变
    //函数后面加const相当于 const per* const this，指向地址的值也不能改了
    void func() const
    {
        //age = 100;
        //会报错，在常函数中不可修改成员属性
        h = 100;
        //当变量加了mutable后，常函数可以修改
    }
};
int main(){
    //在对象前加const,则变成常对象
    //常对象的属性不能被修改（除mutable以外），所以常对象只能调用常函数
    const per p;
    
    return 0;
}
```

