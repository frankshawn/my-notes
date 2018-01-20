# throttle-debounce
> 限制函数的执行频率

## GitHub 地址
[throttle-debounce](https://github.com/niksy/throttle-debounce)

## throttle
> 限制回调函数的执行频率  
```javascript
/**
 * 节流(限制函数的执行频率)
 * @param delay 延迟的时间
 * @param noTrailing 在最后一次调用时是否执行 callback，true 不执行，false 执行
 * @param callback 目标回调函数
 * @param debounceMode
 */
throttle(delay, noTrailing, callback, debounceMode)
```
> dobounceMode: 为 true 时，在被调用时，先执行 callback，在没有被调用时，在指定的延迟之后执行 clear，如果在clear 执行之前继续调用，会重置定时器；为 false 时，在被调用时，不会执行 callback，在指定的延迟之后执行 callback，如果在 callback 执行之前继续调用，会重置定时器

## debounce
> 限制回掉函数的执行频率，但是不同于 debounce 的是，debounce 能保证在一系列调用的时间内，回调函数只执行一次
```javascript
/**
 * 去抖(限制函数的执行频率)
 * @param delay 延迟的时间
 * @param atBegin
 * @param callback 目标回调函数
 */
debounce(delay, atBegin, callback)
```
> atBegin: 为 true 时，在被调用时，会马上执行 callback，如果在延迟时间之前继续调用，不会执行 callback；为 false 时，在被调用时，不会执行 callback，在延迟时间之后会执行 callback，如果在延迟时间之前继续调用，会重置定时器
