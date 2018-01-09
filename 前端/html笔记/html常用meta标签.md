### 设置viewport
`<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no"/>`
*此处：device-width 指代设备的宽度，且是设备独立像素(逻辑像素)的宽度*

### 设置格式检测
`<meta name="format-detection" content="telephone=no"/>
<meta name="format-detection" content="address=no"/>
<meta name="format-detection" content="email=no"/>
<meta name="format-detection" content="telephone=no,address=no,email=no"/>`

### 设置编码
`<meta charset='utf-8' />`

### 禁止浏览器从本地计算机的缓存中访问页面内容
`<meta http-equiv="Pragma" content="no-cache">`

### 页面关键词(SEO)
`<meta name="keywords" content="word" />`

### 页面描述(SEO)
`<meta name="description" content="desc" />`

### 设置搜索引擎索引方式
`<meta name="robots" content="index,follow" />
<!--
    all：文件将被检索，且页面上的链接可以被查询；
    none：文件将不被检索，且页面上的链接不可以被查询；
    index：文件将被检索；
    follow：页面上的链接可以被查询；
    noindex：文件将不被检索；
    nofollow：页面上的链接不可以被查询。
 -->`
