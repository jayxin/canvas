## 描述

HTML5的&lt;canvas&gt;标签用于绘制图像(通过脚本, 通常是JavaScript)。

不过, 该元素(标签)本身并没有绘制能力(它仅仅是图形的容器) - 必须使用脚本来完成实际的绘图任务.

getContext() 可以返回一个绘图环境对象, 该对象提供了用于在画布上绘图的方法和属性。

本手册提供完整的 getContext('2d') 对象属性和方法. 可以用于在画布上绘制文本, 线条, 矩形, 圆形等等.

## 浏览器支持

Internet Explorer 9+, Firefox, Opera, Chrome 以及 Safari 支持 &lt;canvas&gt; 及其属性和方法.

Hint : IE 8 以及更早的版本不支持 该元素。

## 颜色, 样式和阴影

| 属性          | 描述                                     |
| ------------- | ---------------------------------------- |
| fillStyle     | 设置或返回用于填充绘画的颜色, 渐变或模式 |
| strokeStyle   | 设置或返回用于笔触的颜色, 渐变或模式     |
| shadowColor   | 设置或返回用于阴影的颜色                 |
| shadowBlur    | 设置或返回用于阴影的模糊级别             |
| shadowOffsetX | 设置或返回阴影距形状的水平距离           |
| shadowOffsetY | 设置或返回阴影距形状的垂直距离           |

| 方法                   | 描述                                  |
| ---------------------- | ------------------------------------- |
| createLinearGradient() | 创建线性渐变(用在画布内容上)          |
| createPattern()        | 在指定的方向上重复指定的元素          |
| createRadialGradient() | 创建放射状/环形的渐变(用在画布内容上) |
| addColorStop()         | 规定渐变对象中的颜色和停止位置        |

- fillStyle

  ```javascript
  // lang : js
  // 定义用绿色填充的矩形
  var c = document.getElementById("myCanvas");
  var  ctx = c.getContext('2d');
  ctx.fillStyle = '#cce8cf';
  ctx.fillRect(20, 20, 150, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 fillStyle 属性。

  #### 定义和用法

  fillStyle 属性设置或返回用于填充绘画的颜色, 渐变或模式.

  | 默认值  | JS 语法                                           |
  | ------- | ------------------------------------------------- |
  | #000000 | context.fillStyle = color \| gradient \| pattern; |

  ##### 属性值

  | 值       | 描述                                      |
  | -------- | ----------------------------------------- |
  | color    | 指示绘图填充色的CSS颜色值. 默认是#000000. |
  | gradient | 用于填充绘图的渐变对象(线性或放射性)      |
  | pattern  | 用于填充绘图的pattern 对象                |

  ```javascript
  // lang : js
  // 定义从上到下的渐变, 作为矩形的填充样式
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var my_gradient = ctx.createLinearGradient(0, 0, 0, 170);
  my_gradient.addColorStop(0, "black");
  my_gradient.addColorStop(1, "white");
  ctx.fillStyle = my_gradient;
  ctx.fillRect(20, 20, 150, 100);
  ```

  ```javascript
  // lang : js
  // 定义从左到右的渐变, 作为矩形的填充样式
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var my_gradient = ctx.createLinearGradient(0, 0, 170, 0);
  my_gradient.addColorStop(0, "black");
  my_gradient.addColorStop(1, "white");
  ctx.fillStyle = my_gradient;
  ctx.fillRect(20, 20, 150, 100);
  ```

  ```javascript
  // lang : js
  // 定义从黑到红到白的渐变, 作为矩形的填充样式
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var my_gradient = ctx.createLinearGradient(0, 0, 170, 0);
  my_gradient.addColorStop(0, "black");
  my_gradient.addColorStop(0.5, "red");
  my_gradient.addColorStop(1, "white");
  ctx.fillStyle = my_gradient;
  ctx.fillRect(20, 20, 150, 100);
  ```

  ```javascript
  // lang : js
  // 使用图像来填充绘图
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var img = document.getElementById('lamp');
  var pat = ctx.createPattern(img, 'repeat');
  ctx.rect(0, 0, 150, 100);
  ctx.fillStyle = pat;
  ctx.fill();
  ```

- strokeStyle

  ```javascript
  // lang : js
  // 绘制一个矩形, 用蓝色的笔触颜色
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.strokeStyle = '#0000ff';
  ctx.strokeRect(20, 20, 150, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 strokeStyle 属性。

  #### 定义和用法

  strokeStyle 属性设置或返回用于笔触的颜色, 渐变或模式.

  | 默认值  | JS语法                                              |
  | ------- | --------------------------------------------------- |
  | #000000 | context.strokeStyle = color \| gradient \| pattern; |

  ##### 属性值

  | 值       | 描述                                        |
  | -------- | ------------------------------------------- |
  | color    | 指示绘图笔触颜色的CSS颜色值。默认是#000000. |
  | gradient | 用于填充绘图的渐变对象(线性或放射性)        |
  | pattern  | 用于创建 pattern 笔触的 pattern 对象        |

  ```javascript
  // lang : js
  // 使用渐变笔触绘制一个矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var gradient = ctx.createLinearGradient(0, 0, 170, 0);
  gradient.addColorStop("0", "magenta");
  gradient.addColorStop("0.5", "blue");
  gradient.addColorStop("1.0", "red");
  
  // 用渐变进行填充
  ctx.strokeStyle = gradient;
  ctx.lineWidth = 5;
  ctx.strokeRect(20, 20, 150, 100);
  ```

  ```javascript
  // lang : js
  // 使用渐变笔触绘制文本"Hello World"
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.font = '30px Verdana';
  // 创建渐变
  var gradient = ctx.createLinearGradient(0, 0, c.width, 0);
  gradient.addColorStop("0", "magenta");
  gradient.addColorStop("0.5", "blue");
  gradient.addColorStop("1.0", "red");
  // 用渐变进行填充
  ctx.strokeStyle = gradient;
  ctx.strokeText("Hello World", 10, 50);
  ```

- shadowColor

  ```javascript
  // lang : js
  // 绘制一个带有黑色阴影的蓝色矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.shadowBlur = 20;
  ctx.shadowColor = "black";
  ctx.fillStyle = "blue";
  ctx.fillRect(20, 20, 100, 80);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 shadowColor 属性。

  #### 定义和用法

  shadowColor 属性设置或返回用于阴影的颜色.

  Hint : 请将 shadowColor 属性与 shadowBlur 属性一起使用来创建阴影.

  请通过使用 shadowOffsetX 和 shadowOffsetY 属性来调节阴影效果.

  | 默认值  | JS语法                       |
  | ------- | ---------------------------- |
  | #000000 | context.shadowColor = color; |

  ##### 属性值

  | 值    | 描述                                   |
  | ----- | -------------------------------------- |
  | color | 用于阴影的CSS颜色值. 默认值是 #000000. |

- shadowBlur

  ```javascript
  // lang : js
  // 绘制一个带有黑色阴影的蓝色矩形, 模糊级数是20
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.shadowBlur = 20;
  ctx.shadowColor = "black";
  ctx.fillStyle = "blue";
  ctx.fillRect(20, 20, 100, 80);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 shadowBlur 属性。

  #### 定义和用法

  shadowBlur 属性设置或返回阴影的模糊级数.

  | 默认值 | JS语法     |
  | ------ | ---- |
  | #000000 | context.shadowBlur = number; |

  ##### 属性值
  
  | 值     | 描述           |
  | ------ | -------------- |
  | number | 阴影的模糊级数 |
  
- shadowOffsetX

  ```javascript
  // lang : js
  // 绘制一个矩形, 带有向右偏移 20 px 的阴影(从矩形的 left 位置)
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.shadowBlur = 10;
  ctx.shadowOffsetX = 20;
  ctx.shadowColor = "black";
  ctx.fillStyle = "blue";
  ctx.fillRect(20, 20, 100, 80);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 shadowOffsetX 属性。

  #### 定义和用法

  shadowOffsetX 属性设置或返回形状与阴影的水平距离.

  shadowOffsetX = 0 指示阴影位于形状的正下方.

  shadowOffsetX = 20 指示阴影位于形状left 位置右侧的 20 像素处.

  shadowOffsetX = -20 指示阴影位于形状 left 位置左侧的 20 像素处.

  | 默认值 | JS语法                          |
  | ------ | ------------------------------- |
  | 0      | context.shadowOffsetX = number; |

  ##### 属性值

  | 值     | 描述                                   |
  | ------ | -------------------------------------- |
  | number | 正值或负值, 定义阴影与形状的水平距离。 |

- shadowOffsetY

  ```javascript
  // lang : js
  // 绘制一个矩形, 带有向下偏移 20 px 的阴影(从矩形的 top 位置)
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.shadowBlur = 10;
  ctx.shadowOffsetY = 20;
  ctx.shadowColor = "black";
  ctx.fillStyle = "blue";
  ctx.fillRect(20, 20, 100, 80);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 shadowOffsetY 属性。

  #### 定义和用法

  shadowOffsetY 属性设置或返回形状与阴影的垂直距离.

  shadowOffsetY = 0 指示阴影位于形状的正下方.

  shadowOffsetY = 20 指示阴影位于形状top 位置下方的 20 像素处.

  shadowOffsetY = -20 指示阴影位于形状top 位置上方的 20 像素处.

  | 默认值 | JS语法                          |
  | ------ | ------------------------------- |
  | 0      | context.shadowOffsetY = number; |

  ##### 属性值

  | 值     | 描述                                  |
  | ------ | ------------------------------------- |
  | number | 正值或负值, 定义阴影与形状的垂直距离. |

- createLinearGradient()

  ```javascript
  // lang : js
  // 定义从黑到白的渐变(从左向右), 作为矩形的填充样式
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var grd = ctx.createLinearGradient(0, 0, 170, 0);
  grd.addColorStop(0, "black");
  grd.addColorStop(1, "white");
  
  ctx.fillStyle = grd;
  ctx.fillRect(20, 20, 150, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 createLinearGradient() 方法。

  #### 定义和用法

  createLinearGradient() 方法创建线性的渐变对象.

  渐变可以用于填充矩形, 圆形, 线条, 文本等等.

  Hint : 请使用该对象作为 strokeStyle 或 fillStyle 属性的值, 使用 addColorStop() 方法规定不同的颜色, 以及在 gradient 对象中的何处定位颜色.

  ##### JS 语法

  ```javascript
  context.createLinearGradient(x0, y0, x1, y1);
  ```

  ##### 参数值

  | 参数 | 描述                |
  | ---- | ------------------- |
  | x0   | 渐变开始点的 x 坐标 |
  | y0   | 渐变开始点的 y 坐标 |
  | x1   | 渐变结束点的 x 坐标 |
  | y1   | 渐变结束点的 y 坐标 |

  ```javascript
  // lang : js
  // 定义一个渐变(从上到下)作为矩形的填充样式
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var my_gradient = ctx.createLinearGradient(0, 0, 0, 170);
  my_gradient.addColorStop(0, "black");
  my_gradient.addColorStop(1, "white");
  ctx.fillStyle = my_gradient;
  ctx.fillRect(20, 20, 150, 100);
  ```

  ```javascript
  // lang : js
  // 定义一个从黑到红再到白的渐变作为矩形的填充样式
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var my_gradient = ctx.createLinearGradient(0, 0, 170, 0);
  my_gradient.addColorStop(0, "black");
  my_gradient.addColorStop(0.5, "red");
  my_gradient.addColorStop(1, "white");
  ctx.fillStyle = my_gradient;
  ctx.fillRect(20, 20, 150, 100);
  ```

- createPattern()

  ```javascript
  // lang : js
  // 在水平和垂直方向重复图像
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var img = document.getElementById('lamp');
  var pat = ctx.createPattern(img, 'repeat');
  ctx.rect(0, 0, 150, 100);
  ctx.fillStyle = pat;
  ctx.fill();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 createPattern() 方法。

  #### 定义和用法

  createPattern() 方法在指定的方向内重复指定的元素.

  元素可以是图片, 视频, 或者其它canvas元素。

  被重复的元素可以用于绘制/填充矩形, 圆形或线条等等.

  ##### JS 语法

  ```javascript
  context.createPattern(image, "repeat|repeat-x|repeat-y|no-repeat");
  ```

  ##### 参数值

  | 参数      | 描述                               |
  | --------- | ---------------------------------- |
  | image     | 规定要使用的图片, 画布或者视频元素 |
  | repeat    | 默认. 该模式在水平和垂直方向重复.  |
  | repeat-x  | 该模式只在水平方向重复.            |
  | repeat-y  | 该模式只在垂直方向重复.            |
  | no-repeat | 该模式只显示一次(不重复)。         |

- createRadialGradient()

  ```javascript
  // lang : js
  // 在水平和垂直方向重复图像
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var grd = ctx.createRadialGradient(75, 50, 5, 90, 60, 100);
  grd.addColorStop(0, "red");
  grd.addColorStop(1, "white");
  
  ctx.fillStyle = grd;
  ctx.fillRect(10, 10, 150, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 createRadialGradient() 方法。

  #### 定义和用法

  createRadialGradient() 方法创建放射性/圆形渐变对象。(径向渐变)

  渐变可以用于填充矩形, 圆形, 线条, 文本等等.

  Hint : 请使用该对象作为 strokeStyle 或 fillStyle 属性的值, 使用 addColorStop() 方法规定不同的颜色, 以及在 gradient 对象中的何处定位颜色.

  ##### JS 语法

  ```javascript
  context.createRadialGradient(x0, y0, r0, x1, y1, r1);
  ```

  ##### 参数值

  | 参数 | 描述                  |
  | ---- | --------------------- |
  | x0   | 渐变的开始圆的 x 坐标 |
  | y0   | 渐变的开始圆的 y 坐标 |
  | r0   | 开始圆的半径          |
  | x1   | 渐变的结束圆的 x 坐标 |
  | y1   | 渐变的结束圆的 y 坐标 |
  | r1   | 结束圆的半径          |

- addColorStop()

  ```javascript
  // lang : js
  // 定义一个从黑到白的渐变, 作为矩形的填充样式
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var grd = ctx.createLinearGradient(0, 0, 170, 0);
  grd.addColorStop(0, "black");
  grd.addColorStop(1, "white");
  
  ctx.fillStyle = grd;
  ctx.fillRect(20, 20, 150, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 addColorStop() 方法。

  #### 定义和用法

  addColorStop() 方法规定 grdient 对象中的颜色和位置.

  addColorStop() 方法与 createLinearGradient() 或 createRadialGradient() 一起使用。

  Hint: 可以多次调用该方法来改变渐变, 如果不对 gradient 对象使用该方法, 那么渐变将不可见.为了获得可见的渐变, 需要创建至少一个色标.

  ##### JS 语法

  ```javascript
  gradient.addColorStop(stop, color);
  ```

  ##### 参数值

  | 参数  | 描述                                                       |
  | ----- | ---------------------------------------------------------- |
  | stop  | 介于 0. 0 与 1.0 之间的值, 表示渐变中开始与结束之间的位置. |
  | color | 在结束位置显示的 CSS 颜色值                                |

  ```javascript
  // lang : js
  // 通过多个 addColorStop() 方法来定义渐变
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var grd = ctx.createLinearGradient(0, 0, 170, 0);
  grd.addColorStop(0, "black");
  grd.addColorStop("0.3", "magenta");
  grd.addColorStop("0.5", "blue");
  grd.addColorStop("0.6", "green");
  grd.addColorStop("0.8", "yellow");
  grd.addColorStop(1, "red");
  
  ctx.fillStyle = grd;
  ctx.fillRect(20, 20, 150, 100);
  ```

## 线条样式

| 属性       | 描述                                     |
| ---------- | ---------------------------------------- |
| lineCap    | 设置或返回线条的结束端点样式             |
| lineJoin   | 设置或返回两条线相交时, 所创建的拐角类型 |
| lineWidth  | 设置或返回当前的线条宽度                 |
| miterLimit | 设置或返回最大斜接长度                   |

- lineCap

  ```javascript
  // lang : js
  // 绘制线帽
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.beginPath();
  ctx.lineWidth = 10;
  ctx.lineCap = "butt";
  ctx.moveTo(20,20);
  ctx.lineTo(200,20);
  ctx.stroke();
  
  ctx.beginPath();
  ctx.lineCap = "round";
  ctx.moveTo(20,40);
  ctx.lineTo(200,40);
  ctx.stroke();
  
  ctx.beginPath();
  ctx.lineCap = "square";
  ctx.moveTo(20,60);
  ctx.lineTo(200,60);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 lineCap 属性。

  #### 定义和用法

  lineCap 属性设置或返回线条末端线帽的样式.

  注释: "round" 和 "square" 会使线条略微边长.

  | 默认值 | JS语法                                   |
  | ------ | ---------------------------------------- |
  | butt   | context.lineCap = "butt\|round\|square"; |

  ##### 属性值

  | 值     | 描述                                 |
  | ------ | ------------------------------------ |
  | butt   | 默认.向线条的每个末端添加平直的边缘. |
  | round  | 向线条的每个末端添加圆形的线帽       |
  | square | 向线条的每个末端添加正方形线帽       |

- lineJoin

  ```javascript
  // lang : js
  // 当两条线交汇时, 创建圆形边角
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.lineWidth = 10;
  ctx.lineJoin = "round";
  ctx.moveTo(20, 20);
  ctx.lineTo(100, 50);
  ctx.lineTo(20, 100);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 lineJoin 属性。

  #### 定义和用法

  lineJoin 属性设置或返回所创建边角的类型, 当两条线交汇时.

  注释: 值"miter" 受 miterLimit 属性的影响.

  | 默认值 | JS语法                                |
  | ------ | ------------------------------------- |
  | miter  | context.lineJoin="bevelround\|miter"; |

  ##### 属性值

  | 值    | 描述           |
  | ----- | -------------- |
  | bevel | 创建斜角       |
  | round | 创建圆角       |
  | miter | 默认。创建尖角 |

- lineWidth

  ```javascript
  // lang : js
  // 用宽度为 10 px 的线条来绘制矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.lineWidth = 10;
  ctx.strokeRect(20, 20, 80, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 lineWidth 属性。

  #### 定义和用法

  lineWidth 属性设置或返回当前线条的宽度, 以像素计.

  | 默认值 | JS 语法                     |
  | ------ | --------------------------- |
  | 1      | context.lineWidth = number; |

  ##### 属性值

  | 值     | 描述                      |
  | ------ | ------------------------- |
  | number | 当前线条的宽度, 以像素计. |

- miterLimit

  ```javascript
  // lang : js
  // 以最大斜接长度 5 绘制线条
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.lineWidth = 10;
  ctx.lineJoin = "miter";
  ctx.miterLimit = 5;
  ctx.moveTo(20, 20);
  ctx.lineTo(50, 27);
  ctx.lineTo(20, 34);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 miterLimit 属性。

  #### 定义和用法

  miterLimit 属性设置或返回最大斜接长度。

  斜接长度指的是在两条线交汇处内角和外角之间的距离.

  ![miterlimit](miterlimit.gif)

  Hint: 只有当 lineJoin 属性为 "miter" 时, miterLimit 才有效.

  边角的角度越小, 斜接长度就会越大。

  为了避免斜接长度过长, 可以使用 miterLimit 属性.

  如果斜接长度超过 miterLimit 的值, 边角会以 lineJoin 的 "bevel" 类型来显示(图解3):

  ![miterlimet_bevel](miterlimit_bevel.gif)

  | 默认值 | JS 语法                      |
  | ------ | ---------------------------- |
  | 10     | context.miterLimit = number; |

  ##### 属性值

  | 值     | 描述                                                         |
  | ------ | ------------------------------------------------------------ |
  | number | 正数.规定最大斜接长度。如果斜接长度超过 miterLimit 的值, 边角会以 lineJoin 的 "bevel" 类型来显示. |

## 矩形

| 方法         | 描述                         |
| ------------ | ---------------------------- |
| rect()       | 创建矩形                     |
| fillRect()   | 绘制被填充的矩形             |
| strokeRect() | 绘制矩形(无填充)             |
| clearRect()  | 在给定的矩形内清除指定的像素 |

- rect()

  ```javascript
  // lang : js
  // 绘制 150 * 100 像素的矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.rect(20, 20, 150, 100);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 rect() 方法。

  #### 定义和用法

  rect() 方法创建矩形.

  Hint : 请使用 stroke() 或 fill() 方法在画布上实际地绘制矩形.

  ##### JS 语法

  ```javascript
  context.rect(x, y, width, height);
  ```

  ##### 参数值

  | 参数   | 描述                 |
  | ------ | -------------------- |
  | x      | 矩形左上角的 x 坐标  |
  | y      | 矩形左上角的 y 坐标  |
  | width  | 矩形的宽度, 以像素计 |
  | height | 矩形的高度, 以像素计 |

  ```javascript
  // lang : js
  // 通过 rect() 方法来创建三个矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.beginPath();
  ctx.lineWidth = "6";
  ctx.strokeStyle = "red";
  ctx.rect(5, 5, 290, 140);
  ctx.stroke();
  
  ctx.beginPath();
  ctx.lineWidth = "4";
  ctx.strokeStyle = "green";
  ctx.rect(30, 30, 50, 50);
  ctx.stroke();
  
  ctx.beginPath();
  ctx.lineWidth = "10";
  ctx.strokeStyle = "blue";
  ctx.rect(50, 50, 150, 80);
  ctx.stroke();
  ```

- fillRect()

  ```javascript
  // lang : js
  // 绘制 150 * 100 像素已填充矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.fillRect(20, 20, 150, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 fillRect() 方法。

  #### 定义和用法

  fillRect() 方法绘制"已填充"的矩形。默认的填充颜色是黑色。

  Hint: 请使用 fillStyle 属性来设置用于填充绘图的颜色, 渐变或模式。

  ##### JS 语法

  ```javascript
  context.fillRect(x, y, width, height);
  ```

  ##### 参数值

  | 参数   | 描述                 |
  | ------ | -------------------- |
  | x      | 矩形左上角的 x 坐标  |
  | y      | 矩形左上角的 y 坐标  |
  | width  | 矩形的宽度, 以像素计 |
  | height | 矩形的高度, 以像素计 |

- strokeRect()

  ```javascript
  // lang : js
  // 绘制 150 * 100 像素矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.strokeRect(20, 20, 150, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 strokeRect() 方法。

  #### 定义和用法

  strokeRect() 方法绘制矩形(不填充). 笔触的默认颜色是黑色.

  HInt: 请使用 strokeStyle 属性来设置笔触的颜色, 渐变或模式.

  ##### JS 语法

  ```javascript
  context.strokeRect(x, y, width, height);
  ```

  ##### 参数值

  | 参数   | 描述                 |
  | ------ | -------------------- |
  | x      | 矩形左上角的 x 坐标  |
  | y      | 矩形左上角的 y 坐标  |
  | width  | 矩形的宽度, 以像素计 |
  | height | 矩形的高度, 以像素计 |

- clearRect()

  ```javascript
  // lang : js
  // 在给定矩形内清空一个矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.fillStyle = "red";
  ctx.fillRect(0, 0, 300, 150);
  ctx.clearRect(20, 20, 100, 50);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 clearRect() 方法。

  #### 定义和用法

  clearRect() 方法清空给定矩形内的指定像素.

  ##### JS 语法

  ```javascript
  context.clearRect(x, y, width, height);
  ```

  ##### 参数值

  | 参数   | 描述                         |
  | ------ | ---------------------------- |
  | x      | 要清除的矩形左上角的 x 坐标  |
  | y      | 要清除的矩形左上角的 y 坐标  |
  | width  | 要清除的矩形的宽度, 以像素计 |
  | height | 要清除的矩形的高度, 以像素计 |

## 路径

| 方法               | 描述                                                    |
| ------------------ | ------------------------------------------------------- |
| fill()             | 填充当前绘图(路径)                                      |
| stroke()           | 绘制已定义的路径                                        |
| beginPath()        | 起始一条路径, 或重置当前路径                            |
| moveTo()           | 把路径移动到画布中的指定点, 不创建线条                  |
| closePath()        | 创建从当前点回到起始点的路径                            |
| lineTo()           | 添加一个新点, 然后再画布中创建从该点到最后指定点的线条  |
| clip()             | 从原始画布剪切任意形状和尺寸的区域                      |
| quadraticCurveTo() | 创建二次贝塞尔曲线                                      |
| bezierCurveTo()    | 创建三次方贝塞尔曲线                                    |
| arc()              | 创建弧/曲线(用于创建圆形或部分圆)                       |
| arcTo()            | 创建两切线之间的弧/曲线                                 |
| isPointInPath()    | 如果指定的点位于当前路径中, 则返回 true, 否则返回 false |

- fill()

  ```javascript
  // lang : js
  // 绘制矩形,然后用绿色来填色
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.rect(20, 20, 150, 100);
  ctx.fillStyle = "green";
  ctx.fill();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 fill() 方法。

  #### 定义和用法

  fill() 方法填充当前的图像(路径). 默认颜色是黑色.

  Hint: 使用 fillStyle 属性来填充另一种颜色/渐变.

  如果路径未关闭, 那么fill()方法会从路径结束点到开始点之间添加一条线, 以关闭该路径, 然后填充该路径。

  ##### JS 语法

  ```javascript
  context.fill();
  ```

- stroke() 方法

  ```javascript
  // lang : js
  // 绘制一条路径,形状是绿色的字母L
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(20, 20);
  ctx.lineTo(20, 100);
  ctx.lineTo(70, 100);
  ctx.strokeStyle = "green";
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 stroke() 方法。

  #### 定义和用法

  stroke() 方法会实际地绘制出通过moveTo() 和 lineTo() 方法定义的路径.默认颜色是黑色。

  Hint : 请使用 strokeStyle 属性来绘制另一种颜色/渐变.

  ##### JS 语法

  ```javascript
  context.stroke();
  ```

- beginPath()

  ```javascript
  // lang : js
  // 在画布上绘制两条路径
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.beginPath();
  ctx.lineWidth = "5";
  ctx.strokeStyle = "red";
  ctx.moveTo(0, 75);
  ctx.lineTo(250, 75);
  ctx.stroke();
  
  ctx.beginPath();
  ctx.strokeStyle = "blue";
  ctx.moveTo(50, 0);
  ctx.lineTo(150, 130);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 beginPath() 方法。

  #### 定义和用法

  beginPath() 方法开始一条路径, 或重置当前的路径。

  HInt: 使用这些方法来创建路径: moveTo() , lineTo(), quadricCurveTo(), bezierCurveTo(), arcTo() 以及 arc(). 使用 stroke() 方法在画布上绘制确切的路径。

  ##### JS 语法

  ```javascript
  context.beginPath();
  ```

- moveTo()

  ```javascript
  // lang : js
  // 开始一条路径, 移动到位置0, 0. 创建达到位置300, 150的一条线
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(0, 0);
  ctx.lineTo(300, 150);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 moveTo() 方法。

  #### 定义和用法

  ##### JS 语法

  ```javascript
  context.moveTo(x, y);
  ```

  ##### 参数值

  | 参数 | 描述                    |
  | ---- | ----------------------- |
  | x    | 路径的目标位置的 x 坐标 |
  | y    | 路径的目标位置的 y 坐标 |

- closePath()

  ```javascript
  // lang : js
  // 绘制一条路径, 形式是字母L, 然后绘制线条以返回开始点
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(20, 20);
  ctx.lineTo(20, 100);
  ctx.lineTo(70, 100);
  ctx.closePath();
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 closePath() 方法。

  #### 定义和用法

  closePath() 方法创建从当前点到开始点的路径。

  Hint: 使用 stroke() 方法在画布上绘制确切的路径。使用fill() 方法来填充图像(默认是黑色)。使用 fillStyle 属性来填充另一个颜色/渐变。

  ##### JS 语法

  ```javascript
  context.closePath();
  ```

  ```javascript
  // lang : js
  // 绘制绿色三角形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(20, 20);
  ctx.lineTo(20, 100);
  ctx.lineTo(70, 100);
  ctx.closePath();
  ctx.stroke();
  ctx.fillStyle = "#cce8cf";
  ctx.fill();
  ```

- lineTo()

  ```javascript
  // lang : js
  // 开始一条路径, 移动到位置0, 0.创建达到位置300, 150的一条线
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(0, 0);
  ctx.lineTo(300, 150);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 lineTo() 方法。

  #### 定义和用法

  lineTo() 方法添加一个新点, 然后创建从该点到画布中最后指定点的线条(该方法并不会创建线条).

  Hint: 使用 stroke() 方法在画布上绘制确切的路径.

  ##### JS 语法

  ```javascript
  context.lineTo(x, y);
  ```

  ##### 参数值

  | 参数 | 描述                     |
  | ---- | ------------------------ |
  | x    | 路径的目标i位置的 x 坐标 |
  | y    | 路径的目标位置的 y 坐标  |

  ```javascript
  // lang : js
  // 绘制一条路径, 形状是字母L
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(20, 20);
  ctx.lineTo(20, 100);
  ctx.lineTo(70, 100);
  ctx.stroke();
  ```

- clip()

  ```js
  // lang : js
  // 从画布中剪切 200 * 120 像素的矩形区域.然后,绘制绿色矩形.只有被剪切区域内的绿色矩形部分是可见的
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  // 剪切矩形区域
  ctx.rect(50, 20, 200, 120);
  ctx.stroke();
  ctx.clip();
  // 在 clip() 之后绘制绿色矩形
  ctx.fillStyle = "green";
  ctx.fillRect(0, 0, 150, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 clip() 方法。

  #### 定义和用法

  clip() 方法从原始画布中剪切任意形状和尺寸.

  提示: 一旦剪切了某个区域, 则所有之后的绘图都会被限制在被剪切的区域内(不能范文画布上的其它区域)。你也可以在使用clip()方法前通过使用save() 方法对当前画布区域进行保存, 并在以后的任意时间对其进行恢复(通过restore()方法).

  ##### JS 方法

  ```
  context.clip();
  ```

- quadraticCurveTo()

  ```javascript
  // lang : js
  // 绘制一条二次贝塞尔曲线
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(20, 20);
  ctx.quadraticCurveTo(20, 100, 200, 20);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 quadraticCurveTo() 方法。

  #### 定义和用法

  quadraticCurveTo() 方法通过使用表示二次贝塞尔曲线的指定控制带点, 向当前路径添加一个点.

  Hint : 二次贝塞尔曲线需要两个点,第一个点是用于二次贝塞尔计算中的控制点, 第二个点是曲线的结束点. 曲线的开始点是当前路径中最后一个点.若路径不存在, 那么请使用beginPath() 和 moveTo() 方法来定义开始点。

  ![quadraticcurve](quadraticcurve.gif)

  1. 开始点: moveTo(20, 20)
  2. 控制点: quadraticCurveTo(20, 100, 200, 20)
  3. 结束点: quadraticCurveTo(20, 100, 200, 20)

  该方法只有一个控制点。

  ##### JS 语法

  ```javascript
  context.quadraticCurveTo(cpx, cpy, x, y);
  ```

  ##### 参数值

  | 参数 | 描述                  |
  | ---- | --------------------- |
  | cpx  | 贝塞尔控制点的 x 坐标 |
  | cpy  | 贝塞尔控制点的 y 坐标 |
  | x    | 结束点的 x 坐标       |
  | y    | 结束点的 y 坐标       |

- bezierCurveTo()

  ```javascript
  // lang : js
  // 绘制一条三次贝塞尔曲线
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.moveTo(20, 20);
  ctx.bezierCurveTo(20, 100, 200, 100, 200, 20);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 bezierCurveTo() 方法。

  #### 定义和用法

  bezierCurveTo() 方法通过使用表示三次贝塞尔曲线的指定控制点, 向当前路径添加一个点。

  Hint: 三次贝塞尔曲线需要三个点.前两个点是用于三次贝塞尔计算中的控制点,第三个点是曲线的结束点.曲线的开始点是当前路径中最后一个点。如果路径不存在,那么请使用 beginPath() 和 moveTo() 方法来定义开始点。

  ![beziercurve](beziercurve.gif)

  1. 开始点: moveTo(`20`, `20`)
  2. 控制点 1 : bezierCurveTo(`20`, `100`, 200, 100, 200, 20)
  3. 控制点 2 : bezierCurveTo(20, 100, `200`,` 100`, 200, 20)
  4. 结束点 : bezierCurveTo(20, 100, 200, 100, `200`, `20`)

  该曲线有两个控制点。

  ##### JS 语法

  ```javascript
  context.bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y);
  ```

  ##### 参数值

  | 参数 | 描述                        |
  | ---- | --------------------------- |
  | cp1x | 第一个贝塞尔控制点的 x 坐标 |
  | cp1y | 第一个贝塞尔控制点的 y 坐标 |
  | cp2x | 第二个贝塞尔控制点的 x 坐标 |
  | cp2y | 第二个贝塞尔控制点的 y 坐标 |
  | x    | 结束点的 x 坐标             |
  | y    | 结束点的 y 坐标             |

- arc()

  ```javascript
  // lang : js
  // 绘制一个圆形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.arc(100, 75, 50, 0, 2 * Math.PI);
  ctx.stroke();
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 arc() 方法。

  #### 定义和用法

  arc() 方法创建弧/曲线(用于创建圆或部分圆).

  Hint: 如需通过 arc() 来创建圆, 请把起始角设置为 0, 结束角设置为 2 * Math.PI.

  请使用 stroke() 或 fill() 方法在画布上绘制实际的弧。

  ![arc](arc.gif)

  1. 中心: arc(`100`, `75`, 50, 0, 1.5 * Math.PI);
  2. 起始角: arc(100, 75, `0`, 1.5 * Math.PI);
  3. 结束角: arc(100, 75, 0, `1.5 * Math.PI`);

  ##### JS 语法

  ```javascript
  context.arc(x, y, r, sAngle, eAngle, counterclockwise);
  ```

  ##### 参数值

  | 参数             | 值                                                           |
  | ---------------- | ------------------------------------------------------------ |
  | x                | 圆的中心的 x 坐标                                            |
  | y                | 圆的中心的 y 坐标                                            |
  | r                | 圆的半径                                                     |
  | sAngle           | 起始角, 以弧度计(弧的圆形的三点钟位置是0度).                 |
  | eAngle           | 结束角, 以弧度计.                                            |
  | counterclockwise | 可选.规定应该逆时针还是顺时针绘图. false = 顺时针, true = 逆时针. |

- arcTo()

  ```javascript
  // lang : js
  // 在画布上创建介于两个切线之间的弧
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.beginPath();
  ctx.beginPath();
  ctx.moveTo(20, 20); // 创建开始点
  ctx.lineTo(100, 20); // 创建水平线
  ctx.arcTo(150, 20, 150, 70, 50); // 创建弧
  ctx.lineTo(150, 120); // 创建垂直线
  ctx.stroke(); // 进行绘制
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 arcTo() 方法。

  #### 定义和用法

  arcTo() 方法在画布上创建介于两个切线之间的弧 / 曲线.

  Hint: 请使用 stroke() 方法在画布上绘制确切的弧。

  ##### JS 语法

  ```javascript
  context.arcTo(x1, y1, x2, y2, r);
  ```

  ##### 参数值

  | 参数 | 描述              |
  | ---- | ----------------- |
  | x1   | 弧的起点的 x 坐标 |
  | y1   | 弧的起点的 y 坐标 |
  | x2   | 弧的终点的 x 坐标 |
  | y2   | 弧的终点的 y 坐标 |
  | r    | 弧的半径          |

- isPointInPath()

  ```javascript
  // lang : js
  // 绘制一个矩形, 如果点 20, 50 位于当前路径中
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.rect(20, 20, 150, 100);
  if (ctx.isPointInPath(20, 50)) {
      ctx.stroke();
  }
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 isPointInPath() 方法。

  #### 定义和用法

  isPointInPath() 方法返回true, 若指定的点位于当前路径中; 否则返回 false.

  ##### JS 语法

  ```javascript
  context.isPointInPath(x, y);
  ```

  | 参数 | 描述          |
  | ---- | ------------- |
  | x    | 测试的 x 坐标 |
  | y    | 测试的 y 坐标 |


## 转换

| 方法           | 描述                                          |
| -------------- | --------------------------------------------- |
| scale()        | 缩放当前绘图至更大或更小                      |
| rotate()       | 旋转当前绘图                                  |
| translate()    | 重新映射画布上的(0, 0) 位置                   |
| transform()    | 替换绘图的当前转换矩阵                        |
| setTransform() | 将当前转换重置为单位矩阵.然后运行 transform() |

- scale()

  ```javascript
  // lang : js
  // 绘制矩形, 放大到200%, 然后再次绘制矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.strokeRect(5, 5, 25, 15);
  ctx.scale(2, 2);
  ctx.strokeRect(5, 5, 25, 15);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 scale() 方法。

  #### 定义和用法

  scale() 方法缩放当前绘图, 更大或更小.

  Hint: 如果对绘图进行缩放, 所有之后的绘图也会被缩放. 如果scale(2, 2), 那么绘图将定位于距离画布左上角两倍远的位置.

  ##### JS 语法

  ```javascript
  context.scale(scalewidth, scaleheight);
  ```

  ##### 参数值

  | 参数        | 描述                                                        |
  | ----------- | ----------------------------------------------------------- |
  | scalewidth  | 缩放当前绘图的宽度(1 = 100%, 0.5 = 50%, 2 = 200%, 以此类推) |
  | scaleheight | 缩放当前绘图的高度(1 = 100%, 0.5 = 50%, 2 = 200%, etc.)     |

  ```javascript
  // lang : js
  // 绘制一个矩形, 放大到 200%, 再次绘制矩形, 放大到 200%, 然后再次绘制矩形,放大到200%,再次绘制矩形
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.strokeRect(5, 5, 25, 15);
  ctx.scale(2, 2);
  ctx.strokeRect(5, 5, 25, 15);
  ctx.scale(2, 2);
  ctx.strokeRect(5, 5, 25, 15);
  ctx.scale(2, 2);
  ctx.strokeRect(5, 5, 25, 15);
  ```

- rotate()

  ```javascript
  // lang : js
  // 将矩形旋转20度
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.rotate(20 * Math.PI / 180);
  ctx.fillRect(50, 20, 100, 50);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 rotate() 方法。

  #### 定义和用法

  rotate() 方法旋转当前的绘图.

  ##### JS 语法

  ```javascript
  context.rotate(angle);
  ```

  ##### 参数值

  | 参数  | 描述                                                         |
  | ----- | ------------------------------------------------------------ |
  | angle | 旋转角度, 以弧度计. 如需将角度转换为弧度, 请使用 degrees * Math.PI / 180 公式进行计算. |

- translate()

  ```javascript
  // lang : js
  // 在位置(10, 10) 处绘制一个矩形, 将新的(0, 0) 位置设置为 (70, 70).再次绘制新的矩形(注意现在矩形从位置(80, 80) 开始绘制)
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.fillRect(10, 10, 100, 50);
  ctx.translate(70, 70);
  ctx.fillRect(10, 10, 100, 50);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 translate() 方法。

  #### 定义和用法

  translate() 方法重新映射画布上的(0, 0) 位置

  Hint: 当你在 translate() 之后调用诸如 fillRect() 之类的方法时, 值会添加到 x 和 y 坐标值上.

  ##### JS 语法

  ```javascript
  context.translate(x, y);
  ```

  ##### 参数值

  | 参数 | 描述                      |
  | ---- | ------------------------- |
  | x    | 添加到水平坐标 (x) 上的值 |
  | y    | 添加到垂直坐标 (y) 上的值 |

- transform()

  ```javascript
  // lang : js
  // 绘制一个矩形, 通过transform()添加一个新的变换矩阵,再次绘制矩形,添加一个新的变化矩阵,然后再次绘制矩形.注意每当调用transform()时,它都会在前一个变换矩阵上构建
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.fillStyle = 'yellow';
  ctx.fillRect(0, 0, 250, 100);
  
  ctx.transform(1, 0.5, -0.5, 1, 30, 10);
  ctx.fillStyle = "red";
  ctx.fillRect(0, 0, 250, 100);
  
  ctx.transform(1, 0.5, -0.5, 1, 30, 10);
  ctx.fillStyle = 'blue';
  ctx.fillRect(0, 0, 250, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 transform() 方法。

  #### 定义和用法

  画布上的每个对象都拥有一个变换矩阵.

  transform() 方法替换当前的变换矩阵.它以下面描述的矩阵来操作当前的变换矩阵:

  ```
  a	c	e
  b	d	f
  0	0	1
  ```

  换句话说,transform() 允许你缩放,旋转,移动并倾斜当前的环境.

  Hint: 该变换只会影响 transform() 方法调用之后的绘图.

  transform() 方法的行为相对于 rotate, scale() translate() or transform() 完成的其他变换,例如: 若你已经将绘图设置为放到两倍,则transform() 方法会把绘图放大两倍, 绘图最终将放大四倍.

  ##### JS 语法

  ```javascript
  context.transform(a, b, c, d, e, f);
  ```

  ##### 参数值

  | 参数 | 描述         |
  | ---- | ------------ |
  | a    | 水平缩放绘图 |
  | b    | 水平倾斜绘图 |
  | c    | 垂直倾斜绘图 |
  | d    | 垂直缩放绘图 |
  | e    | 水平移动绘图 |
  | f    | 垂直运动绘图 |

- setTransform()

  ```javascript
  // lang : js
  // 绘制一个矩形,通过setTransform() 重置并创建新的变换矩阵,再次绘制矩形,重置并创建新的变换矩阵,然后再次绘制矩形.注意每当调用setTransform()时,它都会重叠前一个变换矩阵然后构建新的矩阵,因此在下面的例子中不会显示红色矩形,因为它在蓝色矩形下面
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.fillStyle = "yellow";
  ctx.fillRect(0, 0, 250, 100);
  
  ctx.setTransform(1, 0.5, -0.5, 1, 30, 10);
  ctx.fillStyle = "red";
  ctx.fillRect(0, 0, 250, 100);
  
  ctx.setTransform(1, 0.5, -0.5, 1, 30, 10);
  ctx.fillStyle = "blue";
  ctx.fillRect(0, 0, 250, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 setTransform() 方法。

  #### 定义和用法

  画布上的每个对象都拥有一个当前的变换矩阵.

  setTransform() 方法把当前的变换矩阵重置为单位矩阵,然后以相同的参数运行 transform().

  换句话说, setTransform() 允许你缩放,旋转,移动并倾斜当前的环境.

  Hint: 该变换只会影响 setTransform() 方法调用之后的绘图,该方法不会相对于其它变换来发生行为.

  ##### JS 语法

  ```javascript
  context.setTransform(a, b, c, d, e, f);
  ```

  ##### 参数值

  | 参数 | 描述         |
  | ---- | ------------ |
  | a    | 水平旋转绘图 |
  | b    | 水平倾斜绘图 |
  | c    | 垂直倾斜绘图 |
  | d    | 垂直缩放绘图 |
  | e    | 水平移动绘图 |
  | f    | 垂直移动绘图 |

## 文本

| 属性         | 描述                                     |
| ------------ | ---------------------------------------- |
| font         | 设置或返回文本内容的当前字体属性         |
| textAlign    | 设置或返回文本内容的当前对齐方式         |
| textBaseline | 设置或返回在绘制文本时使用的当前文本基线 |

- font

  ```javascript
  // lang : js
  // 在画布上写一段 40 px 的文本, 使用字体'Arial'
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.font = '40px Arial';
  ctx.fillText('Hello World', 10, 50);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 fillStyle 属性。

  #### 定义和用法

  font 属性设置或返回画布上文本内容的当前字体属性.

  font 属性使用的语法与CSS的font属性相同.

  | 默认值          | JS 语法                                             |
  | --------------- | --------------------------------------------------- |
  | 10px sans-serif | context.font = "italic small-caps bold 12px arial"; |

  ##### 属性值

  | 值                       | 描述                                                         |
  | ------------------------ | ------------------------------------------------------------ |
  | font-style               | 规定字体样式.可能的值:normal, italic, oblique                |
  | font-variant             | 规定字体变体.可能的值:normal, small-caps                     |
  | font-weight              | 规定字体的粗细.可能的值:normal,bold,bolder.lighter,100,200,300,400,500,600...900 |
  | font-size \| line-height | 规定字号和行高,以像素计.                                     |
  | font-family              | 规定字体系列.                                                |
  | caption                  | 使用标题控件的字体(比如按钮,下拉列表等).                     |
  | icon                     | 使用用于标记图标的字体.                                      |
  | menu                     | 使用用于菜单中的字体(下拉列表和菜单列表)                     |
  | message-box              | 使用用于对话框中的字体.                                      |
  | small-caption            | 使用用于标记小型控件的字体.                                  |
  | status-bar               | 使用用于窗口状态中的字体.                                    |

- textAlign

  ```javascript
  // lang : js
  // 在位置 150 创建一条红线.位置150 是下面例子中定义的所有文本的锚点.研究每种 textAlign 属性值的效果
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  // 在位置 150 创建蓝线
  ctx.strokeStyle = "blue";
  ctx.moveTo(150, 20);
  ctx.lineTo(150, 170);
  ctx.stroke();
  
  ctx.font = '15px Arial';
  
  // 显示不同的 textAlign 值
  ctx.textAlign = "start";
  ctx.fillText("textAlign=start", 150, 60);
  ctx.textAlign = "end";
  ctx.fillText("textAlign=end", 150, 80);
  ctx.textAlign = "left";
  ctx.fillText("textAlign=left", 150, 100);
  ctx.textAlign = "center";
  ctx.fillText("textAlign=center", 150, 120);
  ctx.textAlign = "right";
  ctx.fillText("textAlign=right", 150, 140);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 textAlign 属性。

  #### 定义和用法

  textAlign 属性根据锚点,设置或返回文本内容的当前对齐方式.

  通常,文本会从指定位置开始,不过,如果设置为textAlign="right"并将文本放置到位置150，那么会在位置 150 结束。

  Hint: 使用fillText() 或 strokeText() 方法实际地在画布上绘制并定位文本.

  | 默认值 | JS 语法                                                |
  | ------ | ------------------------------------------------------ |
  | start  | context.textAlign = "center\|end\|left\|right\|start"; |

  ##### 属性值

  | 值     | 描述                          |
  | ------ | ----------------------------- |
  | start  | 默认.文本在指定的位置开始.    |
  | end    | 文本在指定的位置结束.         |
  | center | 文本的中心被放置在指定的位置. |
  | left   | 文本左对齐.                   |
  | right  | 文本右对齐.                   |

- textBaseline

  ```javascript
  // lang : js
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  // 在位置 y = 100 绘制蓝色线条
  ctx.strokeStyle = 'blue';
  ctx.moveTo(5, 100);
  ctx.lineTo(395, 100);
  ctx.stroke();
  
  ctx.font = '20px Arial';
  
  // 在 y = 200 以不同的textBaseline 值放置每个单词
  ctx.textBaseline="top";
  ctx.fillText("Top", 5, 100);
  ctx.textBaseline = "bottom";
  ctx.fillText("Bottom", 50, 100);
  ctx.textBaseline = "middle";
  ctx.fillText("Middle", 120, 100);
  ctx.textBaseline = "alphabetic";
  ctx.fillText("Alphabetic", 190, 100);
  ctx.textBaseline = "hanging";
  ctx.fillText("Hanging", 290, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 textBaseline 属性。

  #### 定义和用法

  textBaseline 属性设置或返回在绘制文本时的当前文本基线.

  下面的图示演示了textBaseline属性支持的各种基线.

  ![textBaseline](textBaseline.gif)

  Hint: fillText() 或 strokeText() 方法在画布上定位文本时,将使用指定的textBaseline值.

  | 默认值     | JS语法                                                       |
  | ---------- | ------------------------------------------------------------ |
  | alphabetic | context.textBaseline = "alphabetic\|top\|hanging\|middle\|ideographic\|bottom"; |

  ##### 属性值

  | 值          | 描述                          |
  | ----------- | ----------------------------- |
  | alphabetic  | 默认.文本基线时普通的字母基线 |
  | top         | 文本基线是 em 方框的顶端.     |
  | hanging     | 文本基线是悬挂基线            |
  | middle      | 文本基线是 em 方框的正中      |
  | ideographic | 文本基线是表意基线            |
  | bottom      | 文本基线是 em 方框的底端.     |

| 方法          | 描述                       |
| ------------- | -------------------------- |
| fillText()    | 在画布上绘制被填充的文本   |
| strokeText()  | 在画布上绘制文本(无填充)   |
| measureText() | 返回包含指定文本宽度的对象 |

- fillText()

  ```javascript
  // lang : js
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.font = '20px Georgia';
  ctx.fillText('Hello World', 10, 50);
  
  ctx.font = '30px Verdana';
  // 创建渐变
  var gradient = ctx.createLinearGradient(0, 0, c.width, 0);
  gradient.addColorStop("0", "magenta")
  gradient.addColorStop("0.5", "blue");
  gradient.addColorStop("1.0", "red");
  // 用渐变填色
  ctx.fillStyle = gradient;
  ctx.fillText("Hello World", 10, 90);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 fillText() 方法。

  #### 定义和用法

  fillText() 方法在画布上绘制填色的文本.文本的默认颜色是黑色.

  Hint: 请使用 font 属性来定义字体和字号,并使用fillStyle 属性以另一种颜色/渐变来渲染文本。

  ##### JS 语法

  ```javascript
  context.fillText(text, x, y, maxWidth);
  ```

  ##### 参数值

  | 参数     | 描述                                  |
  | -------- | ------------------------------------- |
  | text     | 规定在画布上输出的文本                |
  | x        | 开始绘制文本的 x 坐标位置(相对于画布) |
  | y        | 开始绘制文本的 y 坐标位置(相对于画布) |
  | maxWidth | 可选.允许的最大文本宽度,以像素计      |

- strokeText()

  ```javascript
  // lang : js
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.font = '20px Georgia';
  ctx.strokeText('Hello World', 10, 50);
  
  ctx.font = '30px Verdana';
  // 创建渐变
  var gradient = ctx.createLinearGradient(0, 0, c.width, 0);
  gradient.addColorStop("0", "magenta")
  gradient.addColorStop("0.5", "blue");
  gradient.addColorStop("1.0", "red");
  // 用渐变填色
  ctx.strokeStyle = gradient;
  ctx.strokeText("Hello World", 10, 90);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 strokeText() 方法。

  #### 定义和用法

  strokeText() 方法在画布上绘制文本(没有填色).文本的默认颜色是黑色.

  Hint: 请使用font属性来定义字体和字号,并使用strokeStyle 属性以另一种颜色/渐变来渲染文本.

  ##### JS 语法

  ```javascript
  context.strokeText(text, x, y, maxWidth);
  ```

  ##### 参数值

  | 参数     | 描述                                  |
  | -------- | ------------------------------------- |
  | text     | 规定在画布上输出的文本.               |
  | x        | 开始绘制文本的 x 坐标位置(相对于画布) |
  | y        | 开始绘制文本的 y 坐标位置(相对于画布) |
  | maxWidth | 可选.允许的最大文本宽度,以像素计      |

- measureText()

  ```javascript
  // lang : js
  // 在画布上输出文本之前,检查字体的宽度
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.font = "30px Arial";
  var txt = "Hello, World";
  ctx.fillText("width:" + ctx.measureText(txt).width, 10, 50);
  ctx.fillText(txt, 10, 100);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 measureText() 方法。

  #### 定义和用法

  measureText() 方法返回包含一个对象,该对象包含以像素计的指定字体宽度.

  Hint: 若你需要在文本向画布输出之前,就了解文本的宽度,那么请使用该方法.

  ##### JS 语法

  ```javascript
  context.measureText(text).width;
  ```

  | 参数 | 描述         |
  | ---- | ------------ |
  | text | 要测量的文本 |

## 图像绘制

| 方法        | 描述                          |
| ----------- | ----------------------------- |
| drawImage() | 向画布上绘制图像,画布或者视频 |

- drawImage()

  ```javascript
  // lang : js
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var img = document.getElementById('myImg');
  ctx.drawImage(img, 10, 10);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 drawImage() 方法。

  #### 定义和用法

  drawImage() 方法在画布上绘制图像,画布或视频.

  drawImage() 方法也能够绘制图像的某些部分, 以及/或者增加或减少图像的尺寸.

  ##### JS语法1

  ```javascript
  context.drawImage(img, x, y);
  // 在画布上定位图像
  ```

  ##### JS 语法2

  ```javascript
  context.drawImage(img, x, y, width, height);
  // 在画布上定位图像并规定图像的宽度和高度
  ```

  ##### JS语法3

  ```javascript
  context.drawImage(img, sx, sy, swidth, sheight, x, y, width, height);
  // 剪切图像, 并在画布上定位被剪切的部分
  ```

  ##### 参数值

  | 参数    | 描述                                     |
  | ------- | ---------------------------------------- |
  | img     | 规定要使用的图像,画布或视频              |
  | sx      | 可选.开始剪切的 x 坐标位置.              |
  | sy      | 可选.开始剪切的 y 坐标位置.              |
  | swidth  | 可选.被剪切图像的宽度.                   |
  | sheight | 可选.被剪切图像的高度.                   |
  | x       | 在画布上放置图像的 x 坐标位置.           |
  | y       | 在画布是放置图像的 y 坐标位置            |
  | width   | 可选.要使用的图像的宽度(伸展或缩小图像). |
  | height  | 可选.要使用的图像的高度(伸展或缩小图像). |

  ```javascript
  // lang : js
  // 在画布上对图像进行定位,然后规定图像的宽度和高度
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var img = document.getElementById('img');
  ctx.drawImage(img, 10, 10, 240, 160);
  ```

  ```javascript
  // lang : js
  // 剪切图片,并在画布上对被剪切的部分进行定位
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var img = document.getElementById('img');
  ctx.drawImage(img, 90, 130, 90, 80, 20, 20, 90, 80);
  ```

  ```html
  <video id="video1" controls width="270" autoplay>
    <source src="/example/html5/mov_bbb.mp4" type='video/mp4'>
    <source src="/example/html5/mov_bbb.ogg" type='video/ogg'>
    <source src="/example/html5/mov_bbb.webm" type='video/webm'>
  </video>
  ```

  ```javascript
  // lang : js
  // 每 20ms ，代码就会绘制视频的当前帧
  
  var v = document.getElementById('video1');
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var img = document.getElementById('img');
  v.addEventListener('play', function () {
  	var i = window.setInterval(function () {
  		ctx.drawImage(v, 0, 0, 270, 135);
  	}, 20);
  }, false);
  v.addEventListener('pause', function () {
  	window.clearInterval(i);
  }, false);
  v.addEventListener('ended', function () {
  	clearInterval(i);
  }, false);
  ctx.drawImage(img, 90, 130, 90, 80, 20, 20, 90, 80);
  ```

## 像素操作

| 属性   | 描述                                               |
| ------ | -------------------------------------------------- |
| width  | 返回 ImageData 对象的宽度                          |
| height | 返回 ImageData 对象的高度                          |
| data   | 返回一个对象,其包含指定的 ImageData 对象的图像数据 |

- width

  ```javascript
  // lang : js
  // 输出ImageData 对象的宽度
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var imgData = ctx.createImageData(100, 100);
  alert("Width of imgdata is :" + imgData.width);
  for (let i = 0; i < imgData.data.length; i += 4) {
  	imgData.data[i + 0] = 255;
  	imgData.data[i + 1] = 0;
  	imgData.data[i + 2] = 0;
  	imgData.data[i + 3] = 255;
  }
  ctx.putImageData(imgData, 10, 10);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 width 属性。

  #### 定义和语法

  width 属性返回 ImageData 对象的宽度,以像素计算.

  Hint: 请参阅 createImageData(), getImageData(), 以及 putImageData() 以获得更多关于ImageData 对象的知识.

  | 默认值  | JS语法         |
  | ------- | -------------- |
  | #000000 | imgData.width; |

- height

  ```javascript
  // lang : js
  // 输出ImageData 对象的高度
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var imgData = ctx.createImageData(100, 100);
  alert("Height of imgdata is :" + imgData.height);
  for (let i = 0; i < imgData.data.length; i += 4) {
  	imgData.data[i + 0] = 255;
  	imgData.data[i + 1] = 0;
  	imgData.data[i + 2] = 0;
  	imgData.data[i + 3] = 255;
  }
  ctx.putImageData(imgData, 10, 10);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 height 属性。

  #### 定义和用法

  height 属性返回 ImageData 对象的高度, 以像素计.

  | 默认值  | JS 语法         |
  | ------- | --------------- |
  | #000000 | imgData.height; |

- data

  ```javascript
  // lang : js
  // 创建 100 * 100 px 的ImageData 对象, 其中每个像素均被设置为红色
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var imgData = ctx.createImageData(100, 100);
  for (let i = 0; i < imgData.data.length; i+= 4) {
  	imgData.data[i + 0] = 0; // 255
  	imgData.data[i + 1] = 255; // 0
  	imgData.data[i + 2] = 0; // 0
  	imgData.data[i + 3] = 255; // 255
  }
  ctx.putImageData(imgData, 10, 10);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 data 属性。

  #### 定义和用法

  fillStyle 属性设置或返回用于填充绘画的颜色,渐变或模式.

  data 属性返回一个对象, 该对象包含指定的 ImageData 对象的图像数据.

  对于 ImageData 对象中的每个像素, 都存在着四方面的信息, 即RGBA值:

  1. R - 红色(0 - 255)
  2. G - 绿色(0 - 255)
  3. B - 蓝色(0 - 255)
  4. A - alpha 通道(0 - 255, 0 是透明的, 255 是完全可见的)

  color / alpha 以数组的形式存在，并存储于 ImageData 对象的data 属性中.

  ```javascript
  // lang : js
  // 将 ImageData 对象中的第一个像素变为红色的语法
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var imgData = ctx.createImageData(100, 100);
  imgData.data[0] = 255;
  imgData.data[1] = 0;
  imgData.data[2] = 0;
  imgData.data[3] = 255;
  ```

  ```js
  // lang : js
  // 将 ImageData 对象中的第二个像素变为绿色的语法
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var imgData = ctx.createImageData(100, 100);
  imgData.data[4] = 0;
  imgData.data[5] = 255;
  imgData.data[6] = 0;
  imgData.data[7] = 255;
  ```

  ##### JS 语法

  ```js
  imageData.data;
  ```

| 方法              | 描述                                                      |
| ----------------- | --------------------------------------------------------- |
| createImageData() | 创建新的空白的ImageData对象                               |
| getImageData()    | 返回 ImageData 对象, 该对象为画布上指定的矩形复制像素数据 |
| putImageData()    | 把图像数据(从指定的 ImageData 对象)放回画布上             |

- createImageData()

  ```js
  // lang : js
  // 创建 100 * 100 px 的ImageData对象,其中每个像素都是红色的
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var imgData = ctx.createImageData(100, 100);
  for (let i = 0; i < imgData.data.length; i += 4) {
  	imgData.data[i + 0] = 255; 
  	imgData.data[i + 1] = 0;
  	imgData.data[i + 2] = 0;
  	imgData.data[i + 3] = 255;
  }
  ctx.putImageData(imgData, 10, 10);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 createImageData() 方法。

  #### 定义和用法
  
  createImageData() 方法创建新的空白 ImageData 对象. 新对象的默认像素值是 transparent black. 对于 ImageData 对象中的每个像素, 都存在着四方面的信息,即RGBA 值:
  
  1. R - 红色(0 - 255)
  2. G - 绿色(0 - 255)
  3. B - 蓝色(0 - 255)
  4. A - alpha 通道(0 - 255; 0 是透明的, 255 是完全可见的)
  
  因此, transparent black 表示(0, 0, 0, 0).
  
  color / alpha 以数组形式存在,并且既然数组包含了每个像素的四条信息,数组的大小是 ImageData 对象的四倍.(ImageDataObject.data.length)
  
  包含 color / alpha 信息的数组存储于 ImageData 对象的 data 属性中.
  
  Hint : 在操作完成数组中的 color / alpha 信息之后, 可以使用 putImageData() 方法将图像数据拷贝到画布上.
  
  ```javascript
  // lang : js
  // 把 ImageData 对象中的第一个像素变为红色
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  var imgData = ctx.createImageData(100, 100);
  
  imgData.data[0] = 255;
  imgData.data[1] = 0;
  imgData.data[2] = 0;
  imgData.data[3] = 255;
  ```
  
  
  
  ##### JS 语法
  
  有两个版本的 createImageData() 方法:
  
  1. 以指定的尺寸(以像素计) 创建新的 ImageData 对象
  
     ```javascript
     var imgData = context.createImageData(width, height);
     ```
  
  2. 创建与指定的另一个 ImageData 对象尺寸相同的新 ImageData 对象(不会复制图像数据)
  
     ```javascript
     var imgData = context.createImageData(imgageData);
     ```
  
  ##### 参数值
  
  | 参数      | 描述                           |
  | --------- | ------------------------------ |
  | width     | ImageData 对象的宽度, 以像素计 |
  | height    | ImageData 对象的高度, 以像素计 |
  | imageData | 另一个 ImageData 对象          |
  
- getImageData()

  ```js
   // lang : js
  // 通过 getImageData() 复制画布上指定矩形的像素数据，然后通过 putImageData() 将图像数据放回画布
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.fillStyle = "red";
  ctx.fillRect(10, 10, 50, 50);
  
  function copy() {
  	var imgData = ctx.getImageData(10, 10, 50, 50);
  	ctx.putImageData(imgData, 10, 70);
  }
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 getImageData() 方法。

  #### 定义和用法

  getImageData() 方法返回 ImageData 对象, 该对象拷贝了画布指定矩形的像素数据.

  ```
  // 使用该公式遍历所有的像素,并改变其颜色值
  red = 255 - old_red;
  green = 255 - old_green;
  blue = 255 - old_blue;
  ```

  ##### JS 语法

  ```js
  var imgData = context.getImageData(x, y, width, height);
  ```

  ##### 参数值

  | 参数值 | 描述                          |
  | ------ | ----------------------------- |
  | x      | 开始复制的左上角位置的 x 坐标 |
  | y      | 开始复制的左上角位置的 y 坐标 |
  | width  | 将要复制的矩形区域的宽度      |
  | height | 将要复制的矩形区域的高度      |

  ```js
  // lang : js
  // 使用 getImageData() 来反转画布上的图像的每个像素的颜色
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  var img = document.getElementById('img');
  ctx.drawImage(img, 0, 0);
  var imgData = ctx.getImageData(0, 0, c.width, c.height);
  
  for (let i = 0; i < imgData.data.length; i += 4) {
  	imgData.data[i + 0] = 255 - imgData.data[i + 0];
  	imgData.data[i + 1] = 255 - imgData.data[i + 1];
  	imgData.data[i + 2] = 255 - imgData.data[i + 2];
  	imgData.data[i + 3] = 255;
  }
  
  ctx.putImageData(imgData, 0, 0);
  ```

- putImageData()

  #### 浏览器支持

  Internet Explorer 9， Firefox, Opera, Chrome 以及 Safari 支持 putImageData() 方法.

  #### 定义和用法

  putImageData() 方法将图像数据(从指定的 ImageData 对象) 放回画布上.

  ##### JS 语法

  ```javascript
  context.putImageData(imgData, x, y, dirtyX, dirtyY, dirtyWidth, dirtyHeight);
  ```

  ##### 参数值

  | 参数        | 描述                                               |
  | ----------- | -------------------------------------------------- |
  | imgData     | 规定要放回画布的 ImageData 对象.                   |
  | x           | ImageData 对象左上角的 x 坐标, 以像素计            |
  | y           | ImageData 对象左上角的 y 坐标, 以像素计            |
  | dirtyX      | 可选. 水平值(x), 以像素计, 在画布上放置图像的位置. |
  | dirtyY      | 可选. 水平值(y), 以像素计, 在画布上放置图像的位置. |
  | dirtyWidth  | 可选. 在画布上绘制图像所使用的宽度                 |
  | dirtyHeight | 可选. 在画布上绘制图像所使用的高度                 |

## 合成

| 属性                     | 描述                                   |
| ------------------------ | -------------------------------------- |
| globalAlpha              | 设置或返回绘图的当前 alpha 或透明值    |
| globalCompositeOperation | 设置或返回新图像如何绘制到已有的图像上 |

- globalAlpha

  ```js
  // lang : js
  // 绘制一个红色的矩形, 然后将透明度(globalAlpha)设置为0.2,然后再绘制一个绿色和一个蓝色的矩形
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  ctx.fillStyle = 'red';
  ctx.fillRect(20, 20, 75, 50);
  // 调节透明度
  ctx.globalAlpha = 0.2;
  ctx.fillStyle = 'blue';
  ctx.fillRect(50, 50, 75, 50);
  ctx.fillStyle = 'green';
  ctx.fillRect(80, 80, 75, 50);
  ```

  #### 浏览器支持

  Internet Exporer 9, Firefox, Opera, Chrome 以及 Safari 支持该属性.

  #### 定义和用法

  globalAlpha 属性设置或返回绘图的当前透明值(alpha 或 transparency).

  globalAlpha 属性值必须是介于 0.0 (完全透明) 与 1.0 (不透明) 之间的数字.

  | 默认值 | JS 语法                       |
  | ------ | ----------------------------- |
  | 1.0    | context.globalAlpha = number; |

  ##### 属性值

  | 值     | 描述                              |
  | ------ | --------------------------------- |
  | number | 透明值. 必须介于 0.0 与 1.0 之间. |

- globalCompositeOperation

  ```javascript
  // lang : js
  // 使用不同的 globalCompositeOperation 值绘制矩形, 红色矩形是目标图像,蓝色是源图像
  
  var c = document.getElementById('myCanvas');
  var ctx = c.getContext('2d');
  
  ctx.fillStyle = 'red';
  ctx.fillRect(20, 20, 75, 50);
  ctx.globalCompositeOperation = "source-over";
  ctx.fillStyle = 'blue';
  ctx.fillRect(50, 50, 75, 50);
  
  ctx.fillStyle = 'red';
  ctx.fillRect(150, 20, 75, 50);
  ctx.globalCompositeOperation = "destination-over";
  ctx.fillStyle = 'blue';
  ctx.fillRect(180, 50, 75, 50);
  ```

  #### 浏览器支持

  Internet Explorer 9、Firefox、Opera、Chrome 以及 Safari 支持 globalCompositeOperation 属性。

  #### 定义和用法

  globalCompositeOperation 属性设置或返回如何将一个源(新的)图像绘制到目标(已有)图像上.

  源图像 = 打算放置到画布上的绘图.

  目标图像 = 已经放置在画布上的绘图.

  | 默认值      | JS语法                                          |
  | ----------- | ----------------------------------------------- |
  | source-over | context.globalCompositeOperation = "source-in"; |

  ##### 属性值

  | 值               | 描述                                                         |
  | ---------------- | ------------------------------------------------------------ |
  | source-over      | 默认.在目标图像上显示源图像.                                 |
  | source-atop      | 在目标图像顶部显示源图像.源图像位于目标图像之外的部分是不可见的. |
  | source-in        | 在目标图像中显示源图像.只有目标图像内的源图像部分会显示,目标图像是透明的. |
  | source-out       | 在目标图像之外显示源图像.只会显示目标图像之外源图像部分,目标图像是透明的. |
  | destination-over | 在源图像上方显示目标图像.                                    |
  | destination-atop | 在源图像顶部显示目标图像.源图像之外的目标图像部分不会被显示. |
  | destination-in   | 在源图像中显示目标图像.只有源图像内的目标图像部分会被显示,源图像是透明的. |
  | destination-out  | 在源图像外显示目标图像.只有源图像外的目标图像部分会被显示,源图像是透明的. |
  | lighter          | 显示源图像 + 目标图像.                                       |
  | copy             | 显示源图像.忽略目标图像.                                     |
  | xor              | 使用异或操作对源图像与目标图像进行组合.                      |

  ```javascript
  // lang : js
  // 所有 globalCompositeOperation 属性值：
  
  var gco = new Array();
  gco.push('source-atop');
  gco.push('source-in');
  gco.push('source-out');
  gco.push('source-over');
  gco.push('destination-atop');
  gco.push('destination-in');
  gco.push('destination-out');
  gco.push('destination-over');
  gco.push('lighter');
  gco.push('copy');
  gco.push('xor');
  
  for (let i = 0; i < gco.length; ++i) {
  	document.write('<div id="p_' + i + '" style="float: left;">' + gco[i] + ':<br>');
  	var c = document.createElement('canvas');
  	c.width = 120;
  	c.height = 100;
  	document.getElementById('p_' + i).appendChild(c);
  	var ctx = c.getContext('2d');
  	ctx.fillStyle = 'blue';
  	ctx.fillRect(10, 10, 50, 50);
  	ctx.globalCompositeOperation = gco[i];
  	ctx.beginPath();
  	ctx.fillStyle = 'red';
  	ctx.arc(50, 50, 30, 0, 2 * Math.PI);
  	ctx.fill();
  	document.write("</div>");
  }
  ```

## 其它

| 方法          | 描述                           |
| ------------- | ------------------------------ |
| save()        | 保存当前环境的状态             |
| restore()     | 返回之前保存过的路径状态和属性 |
| createEvent() |                                |
| getContext()  |                                |
| toDataURL()   |                                |