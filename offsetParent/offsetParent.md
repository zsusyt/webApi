# 定位父级offsetParent的定义是：与当前元素最近的经过定位(position不等于static)的父级元素，主要分为下列几种情况:
## 【1】元素自身有fixed定位，offsetParent的结果为null
### firefox浏览器有兼容问题：firefox并没有考虑固定定位的问题，返回<body>，其他浏览器都返回null
## 【2】元素自身无fixed定位，且父级元素都未经过定位，offsetParent的结果为<body>
## 【3】元素自身无fixed定位，且父级元素存在经过定位的元素，offsetParent的结果为离自身元素最近的经过定位的父级元素
## 【4】<body>元素的parentNode是null
##  IE7浏览器有一些列bug，应该不用考虑了

以上内容主要参考这个[链接](http://www.cnblogs.com/xiaohuochai/p/5828369.html)
里面还有针对offsetWidth、offsetHeight、offsetTop、offsetLeft的讲解。

要知道某个元素在页面上的偏移量，将这个元素的offsetLeft和offsetTop与其offsetParent的相同属性相加，并加上offsetParent的相应方向的边框，如此循环直到根元素，就可以得到元素到页面的偏移量

这个[链接](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLElement/offsetParent)是MDN的