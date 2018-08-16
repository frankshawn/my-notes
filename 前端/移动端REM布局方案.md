**场景：**
1. 设计稿按照 750px 设计
1. html 基准字体大小为 100px
1. 页面最大宽度为 750px
1. 页面最小宽度为 320px

## REM 自适应工具类
1.安装throttle-debounce，执行：cnpm install -S throttle-debounce
2.复制如下代码（typescript）：
```typescript
declare const window: any
declare const document: any

const debounce = require('throttle-debounce/debounce')

export class RemResponsiveUtils {
    static baseFontSize = 100
    static baseDocWidth = 750
    static maxDocWidth = 750
    static minDocWidth = 320

    static onResize () {
        let docWidth: number = document.documentElement.clientWidth
        if (docWidth > RemResponsiveUtils.maxDocWidth) {
            docWidth = RemResponsiveUtils.maxDocWidth
        } else if (docWidth < RemResponsiveUtils.minDocWidth) {
            docWidth = RemResponsiveUtils.minDocWidth
        }
        document.querySelector('html').style.fontSize = (docWidth / RemResponsiveUtils.baseDocWidth) * RemResponsiveUtils.baseFontSize + 'px'
    }

    static init () {
        RemResponsiveUtils.onResize()
        window.onresize = debounce(500, RemResponsiveUtils.onResize)
    }
}
```
3.执行 `RemResponsive.init()`
