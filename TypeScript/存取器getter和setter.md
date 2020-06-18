使用 `getter` 和 `setter` 可以改变属性的赋值和读取行为。

例1：

```js
class Animal {
    constructor(name) {
        this.name = name
    }

    get name() {
        return 'Jack'
    }

    set name(value) {
        console.log('setter:', value)
    }
}

let a = new Animal('Kitty') // setter: Kitty
a.name = 'Tom' // setter: Tom
console.log(a.name) // Jack
```

我们可以看到 `setter` 中并没有将value值赋给 `getter` 中的返回值，因此，`new Animal('Kitty')`只是将`Kitty` 赋给 `setter` 中的参数value，`a.name= 'Tom'`也只是将`Tom` 赋给 `setter` 中的参数value。

此时打印 `a.name` 得到的还是最开始的 `Jack`。


例2：

```js
let passcode = "scret passcode"

class Employee {
    // 定义 _fullName
    private _fullName: string

    // 获取 _fullName
    get fullName(): string {
        return this._fullName
    }

    // 设置_fullName
    set fullName(newName: string) {
        if(passcode && passcode === 'secret passcode') {
            this._fullName = newName
        } else {
            console.log("Error: Unauthorized update of employee!")
        }
    }

}
// 实例化class
let employee = new Employee()

// 触发setter方法， 将 Bob Smith 作为 fullName函数的参数
employee.fullName = "Bob Smith"

if(employee.fullName) {
    alert(employee.fullName)
}
```

