### 将 base64 字符串转换成文件
```js
function base64ToFile (b64Data, contentType) {
	contentType = contentType || ''
	const sliceSize = 512
	const byteCharacters = atob(b64Data)
	const byteArrays = []
	for (let offset = 0; offset < byteCharacters.length; offset += sliceSize) {
	  const slice = byteCharacters.slice(offset, offset + sliceSize)
	  const byteNumbers = new Array(slice.length)
	  for (let i = 0; i < slice.length; i++) {
	    byteNumbers[ i ] = slice.charCodeAt(i)
	  }
	  const byteArray = new Uint8Array(byteNumbers)
	  byteArrays.push(byteArray)
	}
	return new File(byteArrays, 'image.png', { type: contentType })
}
```

### 打印日志
```js
function _log(info) {
    var loggerDom = document.querySelector("#logger");
    var loggerTitle = null;
    if(!loggerDom) {
        loggerDom = document.createElement("div");
        loggerDom.id = "logger";
        loggerTitle = document.createElement("p");
        loggerTitle.innerHTML = "日志标题:";
        loggerTitle.style.cssText = "color:blue;font-weight:bold";
        loggerDom.appendChild(loggerTitle);
        document.querySelector("body").appendChild(loggerDom);
    }
    var pDom = document.createElement("p");
    pDom.innerHTML = new Date().toISOString() + ":<span style='color:red;font-weight:bold;'>" + info + "</span>";
    loggerDom.insertBefore(pDom, loggerDom.childNodes[1]);
}
```

### 显示精确到天的倒计时
```js
/**
 * 显示精确到天的倒计时
 * @param timeStr 日期字符串，格式：2017年04月30日09时00分11秒
 * @param currDate 当前时间的 Date 对象
 */
function showCountdownAccurateToDate (timeStr, currDate) {
  const TOTAL_TIME_FOR_SECOND = 1000
  const TOTAL_TIME_FOR_MINUTE = TOTAL_TIME_FOR_SECOND * 60
  const TOTAL_TIME_FOR_HOUR = TOTAL_TIME_FOR_MINUTE * 60
  const TOTAL_TIME_FOR_DAY = TOTAL_TIME_FOR_HOUR * 24
  let time = new Date(timeStr.replace(/[年月]/g, '/').replace(/[日秒]/g, ' ').replace(/[时分秒]/g, ':').substring(0, 19)).getTime()
  let nowTime = currDate.getTime()
  let timeDiff = time - nowTime
  let showStr = []
  if (time - nowTime > 0) {
    let day = parseInt(timeDiff / TOTAL_TIME_FOR_DAY)
    let hour = parseInt((timeDiff - day * TOTAL_TIME_FOR_DAY) / TOTAL_TIME_FOR_HOUR)
    let minute = parseInt((timeDiff - day * TOTAL_TIME_FOR_DAY - hour * TOTAL_TIME_FOR_HOUR) / TOTAL_TIME_FOR_MINUTE)
    let second = parseInt((timeDiff - day * TOTAL_TIME_FOR_DAY - hour * TOTAL_TIME_FOR_HOUR - minute * TOTAL_TIME_FOR_MINUTE) / TOTAL_TIME_FOR_SECOND)
    showStr.push(day + '天')
    showStr.push(hour + '时')
    showStr.push(minute + '分')
    showStr.push(second + '秒')
    return showStr.join('')
  } else {
    return timeStr
  }
}
```
