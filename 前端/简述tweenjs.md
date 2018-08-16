## 基础资料
1. 官方 user guide：[https://github.com/tweenjs/tween.js/blob/master/docs/user_guide.md](https://github.com/tweenjs/tween.js/blob/master/docs/user_guide.md)
1. [GitHub地址](https://github.com/tweenjs/tween.js)

## 安装
执行 `cnpm i -S @tweenjs/tween.js`


## 简单DEMO

```javascript
const TWEEN = require('@tweenjs/tween.js')

class Demo {
    animate () {
        this.animate = this.animate.bind(this)
        requestAnimationFrame(this.animate)
        TWEEN.update()
    }

    init () {
        const tween = new TWEEN.Tween({ number: 0 }).to({ number: 1000 }, 1000).easing(TWEEN.Easing.Linear.None).start()
        tween.onUpdate((data: any) => {
            console.log(data.number)
        })
        this.animate()
    }
}
```


## 注意事项
1. 关于 TWEEN.update() 的参数
> TWEEN.update() 可传入 time 参数，在自定义 time 参数时，需在调用 tween.start() 函数时，传入初始 time 值，否则，tween 在执行时，默认 startTime 的值是 start 函数执行时 TWEEN.now() 的返回值，从而导致当前 tween 的补间动画延迟执行，延迟执行的时间取决于当前 tween 对应的 startTime 的值和 TWEEN.update(time) 函数中 time 的增量值的幅度。示例代码如下：

 ```javascript
  class Demo {
      time = 0

      animate () {
          this.animate = this.animate.bind(this)
          requestAnimationFrame(this.animate)
          TWEEN.update(this.time)
          this.time += 100
      }

      init () {
          const tween = new TWEEN.Tween({ number: 0 }).to({ number: 1000 }, 1000).easing(TWEEN.Easing.Linear.None).start(this.time)
          tween.onUpdate((data: any) => {
              console.log(data.number)
          })
          this.animate()
      }
  }
```
