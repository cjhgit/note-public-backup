# 类

类（Class）

```javascript
class Fruit {
    constructor() {
        console.log('我是水果')
    }
}

class Apple extends Fruit {
    constructor() {
        super()
        console.log('我是苹果')
    }
}

new Apple()
```

输出：

```javascript
我是水果
我是苹果
```

