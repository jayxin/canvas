```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style type="text/css">
		body {
			text-align : center;
			padding-top : 20px;
		}
		canvas {
			box-shadow : 0 0 10px #333;
			margin : 0 auto;
		}
	</style>
</head>
<body onload="draw()"> <!-- 模板 -->
	<canvas id="canvas" width="800" height="600">
		Your browser is not supported!!!
	</canvas>
	<script type="text/javascript">
		function draw() {
			var canvas = document.getElementById('canvas');
			if (canvas.getContext) {
				var ctx = canvas.getContext('2d');
			}
		}
	</script>
</body>
</html>
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        /*ctx.fillStyle = 'rgb(200, 0, 0)';
        ctx.fillRect(10, 10, 350, 300); // 填充矩形

        ctx.fillStyle = 'rgba(0, 0, 200, 0.5)';
        ctx.fillRect(30, 30, 350, 300);*/

        ctx.strokeStyle = 'rgb(200, 0, 0)';
        ctx.strokeRect(10, 10, 350, 300); // 描边矩形

        ctx.strokeStyle = 'rgba(0, 0, 200, 0.5)';
        ctx.strokeRect(30, 30, 350, 300);
    }
}
```

```javascript
// lang: js
// 清除矩形
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        /*
        * 绘制一个填充的矩形
        * fillRect(x, y, width, height)

        * 绘制一个描边的矩形
        * strokeRect(x, y, width, height)

        * 清除指定矩形区域
        * clearRect(x, y, width, height);
        */
        ctx.fillRect(25, 25, 100, 100);
        ctx.clearRect(45, 45, 60, 60); // 清除矩形
        ctx.strokeRect(50, 50, 50, 50);
    }
}
```

```javascript
// 绘制路径
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        /*
        * 以上三种方法都是用于绘制矩形的

        * 如何通过路径绘制图形

        * 平面图形的基本元素就是路径
        * 1. 创建起始路径
        * 2. 使用画图命令画出路径
        * 3. 把路径闭合
        * 4. 通过描边或者填充绘制图形
        */

        // 绘制一个三角形
        ctx.beginPath();
        ctx.moveTo(75, 50); // 起始点x, ys
        ctx.lineTo(100, 75);
        ctx.lineTo(100, 25);
        //ctx.lineTo(75, 50);

        //ctx.fill();

        ctx.closePath(); // 闭合
        ctx.stroke();
    }
}
```

```javascript
// lang: js
// 绘制两个三角形
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        ctx.beginPath();
        ctx.moveTo(25, 25);
        ctx.lineTo(105, 25);
        ctx.lineTo(25, 105);
        ctx.fill();

        ctx.beginPath();
        ctx.moveTo(125, 125);
        ctx.lineTo(125, 45);
        ctx.lineTo(45, 125);
        ctx.closePath();
        ctx.stroke();
    }
}
```

```javascript
// lang: js
// 绘制圆形
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // 圆的组成: 圆心, 半径, 开始角度, 结束角度, 顺时针/逆时针
        ctx.strokeStyle = 'orange';
        ctx.lineWidth = 10;

        // 画圆
        //ctx.arc(x, y, radius, startAngle(0, 三点钟), endAngle, anticlockwise(默认是false顺时针));
        //ctx.arc(400, 300, 150, 0, Math.PI * 2, false);
        //ctx.arc(400, 300, 150, 0, Math.PI / 2, true);
        //ctx.arc(400, 300, 150, 0, Math.PI / 2, false);
        ctx.arc(400, 300, 300, -Math.PI / 2, Math.PI);
        ctx.stroke();
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // 循环建圆
        for (let i = 0; i < 4; ++i) {
            for (let j = 0; j < 3; ++j) {
                ctx.beginPath();
                var x = 25 + j * 50,
                    y = 25 + i * 50,
                    radius = 20,
                    startAngel = 0,
                    endAngel = Math.PI + (Math.PI * j) / 2,
                    anticlockwise = (i % 2) == 0 ? false : true;

                ctx.arc(x, y, radius, startAngel, endAngel, anticlockwise);
                if (i < 2) {
                    ctx.stroke();
                } else {
                    ctx.fill();
                }
            }
        }
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // smile
        ctx.beginPath();
        ctx.arc(75, 75, 50, 0, Math.PI * 2, true);
        ctx.moveTo(110, 75);
        ctx.arc(75, 75, 35, 0, Math.PI, false);
        ctx.moveTo(65, 65);
        ctx.arc(60, 65, 5, 0, Math.PI * 2, true);
        ctx.moveTo(95, 65);
        ctx.arc(90, 65, 5, 0, Math.PI * 2, true);
        ctx.stroke();
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        /*
        * 线性渐变
        * 参数1: 起点x1
        * 参数2: 起点y1
        * 参数3: 终点x2
        * 参数4: 终点y2
        */

        var lingrad = ctx.createLinearGradient(0, 0, 0, 150);

        /*
        * 添加颜色
        * 参数1: 必须是0.0 - 1.0之间的数值,数值表示颜色所在的相对位置
        * 参数2: 颜色, white #fff #ffffff rgb(255, 255, 255)
        */
        lingrad.addColorStop(0, '#cc6677');
        lingrad.addColorStop(0.5, '#fff');
        lingrad.addColorStop(0.5, '#c6c776');
        lingrad.addColorStop(1, '#fff');

        var lingrad2 = ctx.createLinearGradient(0, 50, 0, 90);
        lingrad2.addColorStop(0.5, '#000');
        lingrad2.addColorStop(1, 'rgba(0, 0, 0, 0)');

        ctx.fillStyle = lingrad;
        ctx.fillRect(10, 10, 130, 130);

        ctx.strokeStyle = lingrad2;
        ctx.strokeRect(50, 50, 50, 50);
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        /*
         * 径向渐变
         * 参数1: x1轴		参数1和参数2代表第一个圆的圆心
         * 参数2: y1轴
         * 参数3: r1半径
         * 参数4: x2轴		参数1和参数2代表第一个圆的圆心
         * 参数5: y2轴
         * 参数6: r2半径
        */

        var radgrad = ctx.createRadialGradient(50, 50, 10, 50, 50, 30);
        // radgrad = ctx.createRadialGradient(45, 45, 10, 52, 50, 30);

        radgrad.addColorStop(0, '#a7d30c');
        radgrad.addColorStop(0.9, '#019f62');
        radgrad.addColorStop(1, 'rgba(1, 159, 98, 0)');

        ctx.fillStyle = radgrad;
        ctx.fillRect(0, 0, 150, 150);

        var radgrad2 = ctx.createRadialGradient(105, 105, 20, 112, 120, 50);

        radgrad2.addColorStop(0, '#ff5f98');
        radgrad2.addColorStop(0.9, '#ff0188');
        radgrad2.addColorStop(1, 'rgba(255, 1, 136, 0)');

        ctx.fillStyle = radgrad2;
        ctx.fillRect(0, 0, 150, 150);
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // 绘制图片
        var img = new Image();
        img.src = 'image.png';

        img.onload = function () {
            var ptrn = ctx.createPattern(img, 'repeat-x');
            ctx.fillStyle = ptrn;
            ctx.fillRect(0, 0, 800, 600);
            // 在绘制图片时一定要保证图像被加载完成
        }
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // 绘制文字阴影
        var lingrad = ctx.createLinearGradient(100, 200, 300, 200);
        lingrad.addColorStop(0.5, '#cc6677');
        lingrad.addColorStop(1, '#000');

        ctx.shadowColor = 'orange'; // 阴影的颜色
        ctx.shadowBlur = 10; 
        ctx.shadowOffsetX = 20; // 在x轴上的偏移量
        ctx.shadowOffsetY = 20; // 在y轴上的偏移量

        ctx.font = 'bold italic 160px arial';
        /*
        * font-weight
        * font-style
        * font-size
        * font-family
        */

        ctx.fillStyle = lingrad;
        ctx.fillText('Henry', 100, 200);
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // DrawImage
        var img = new Image();
        img.src = 'image.jpg';

        img.onload = function () {
            ctx.drawImage(this, 0, 0);
            /*
            * 参数1: 图像
            * 参数2: x轴
            * 参数3: y轴
            * 参数4: 宽度
            * 参数5: 高度
            * 参数6: 绘制的x轴
            * 参数7: 绘制的y轴
            * 参数8: 绘制的宽度
            * 参数9: 绘制的高度
            */
            ctx.drawImage(this, 0, 0, 120, 100, 150, 50, 100, 50);
        }
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // Clip
        var img = new Image();
        img.src = 'image.jpg';

        img.onload = function () {
            ctx.beginPath();
            ctx.arc(400, 300, 150, 0, Math.PI * 2);
            ctx.fill();
            ctx.clip();
            ctx.drawImage(this, 150, 140);
        }
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // 涂鸦
        // 添加鼠标按下事件
        canvas.onmousedown = function (e) {
            let ev = e || window.event;
            let x = ev.clientX - canvas.offsetLeft,
                y = ev.clientY - canvas.offsetTop;

            ctx.strokeStyle = 'green';
            ctx.lineWidth = 10;

            ctx.beginPath();
            ctx.moveTo(x, y);

            canvas.onmousemove = function (e) {
                let ev = e || window.event;
                let x = ev.clientX - canvas.offsetLeft,
                    y = ev.clientY - canvas.offsetTop;

                ctx.lineTo(x, y);
                ctx.stroke();
            }

            canvas.onmouseup = function () {
                canvas.onmousemove = ""; // null
            }
        }
    }
}
```

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style type="text/css">
		body, html {
			/*text-align : center;
			padding-top : 20px;*/
			margin : 0;
		}
		canvas {
			/*box-shadow : 0 0 10px #333;
			margin : 0 auto;*/
			position : absolute;
			left : 0;
		}
	</style>
</head>
<body onload="draw()">

	<img src="image.jpg" alt="">
	<canvas id="canvas" width="800" height="600">
		Your browser is not supported!!!
	</canvas>
	<script type="text/javascript">
		function draw() {
			var canvas = document.getElementById('canvas');
			if (canvas.getContext) {
				var ctx = canvas.getContext('2d');

				ctx.beginPath();
				ctx.fillStyle = 'gray';
				ctx.fillRect(0, 0, canvas.width, canvas.height);
				ctx.globalCompositeOperation = 'destination-out';
				// you are my destiny
				ctx.lineWidth = 20;
				ctx.lineCap = 'round';

				canvas.onmousedown = function (e) {
					let ev = e || window.event;
					let x = ev.clientX,
						y = ev.clientY;

						ctx.moveTo(x, y);

						canvas.onmousemove = function (e) {
							let ev = e || window.event;
							let x = ev.clientX,
								y = ev.clientY;

							ctx.lineTo(x, y);
							ctx.stroke();
						}

						canvas.onmouseup = function () {
							canvas.onmousemove = "";
						}
				}
			}
		}
	</script>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style type="text/css">
		body {
			text-align : center;
			padding-top : 20px;
		}
		canvas {
			box-shadow : 0 0 10px #333;
			/*margin : 0 auto;*/
		}
	</style>
</head>
<body onload="draw()"> <!-- 模板 -->
	<canvas id="canvas1" width="300" height="300">
		Your browser is not supported!!!
	</canvas>
	<canvas id="canvas2" width="300" height="300">
		Your browser is not supported!!!
	</canvas>
	<canvas id="canvas3" width="300" height="300">
		Your browser is not supported!!!
	</canvas>
	<canvas id="canvas4" width="300" height="300">
		Your browser is not supported!!!
	</canvas>

	<script type="text/javascript">
		function draw() {
			var canvas1 = document.getElementById('canvas1');
			var canvas2 = document.getElementById('canvas2');
			var canvas3 = document.getElementById('canvas3');
			var canvas4 = document.getElementById('canvas4');
			if (canvas1.getContext) {
				var ctx1 = canvas1.getContext('2d');

				ctx1.beginPath();
				ctx1.fillStyle = 'red';
				ctx1.fillRect(50, 50, 100, 100);

				// 图像混合
				ctx1.globalCompositeOperation = 'destination-over';
				ctx1.fillStyle = 'green';
				ctx1.arc(150, 150, 50, 0, Math.PI * 2);
				ctx1.fill();

				/*
				* 目标图像: 画布上已经存在的图像
				* 源图像: 即将画到画布上的图像
				* source-over: 重叠区域源图像覆盖目标图像
				* destination-over: 重叠区域目标图像覆盖源图像
				*/

				// 画布2
				var ctx2 = canvas2.getContext('2d');

				ctx2.beginPath();
				ctx2.fillStyle = 'red';
				ctx2.fillRect(50, 50, 100, 100);

				// 图像混合
				ctx2.globalCompositeOperation = 'source-atop';
				ctx2.fillStyle = 'green';
				ctx2.arc(150, 150, 50, 0, Math.PI * 2);
				ctx2.fill();

				/*
				* source-atop: 只显示与目标图像重叠的部分
				* destination-atop: 只显示与源图像重叠的部分
				*/

				// 画布3
				var ctx3 = canvas3.getContext('2d');

				ctx3.beginPath();
				ctx3.fillStyle = 'red';
				ctx3.fillRect(50, 50, 100, 100);

				// 图像混合
				ctx3.globalCompositeOperation = 'source-in';
				ctx3.fillStyle = 'green';
				ctx3.arc(150, 150, 50, 0, Math.PI * 2);
				ctx3.fill();
				/*
				* source-in: 只显示与目标图像重叠部分的源图像，目标图像不显示
				* destination-in: 只显示与源图像重叠部分的目标图像，源图像不显示
				*/

				// 画布4
				var ctx4 = canvas4.getContext('2d');

				ctx4.beginPath();
				ctx4.fillStyle = 'red';
				ctx4.fillRect(50, 50, 100, 100);

				// 图像混合
				ctx4.globalCompositeOperation = 'source-out';
				ctx4.fillStyle = 'green';
				ctx4.arc(150, 150, 50, 0, Math.PI * 2);
				ctx4.fill();
				/*
				* source-out: 重叠部分不显示，显示不重叠的源图像
				* destination-out: 重叠部分不显示，显示不重叠的目标图像
				*/
			}
		}
	</script>
</body>
</html>
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // 矩形直线运动 animate
        ctx.beginPath();
        /*
        * canvas 的动画原理
        * 1. 绘制图像
        * 2. 清除图像
        * 3. 更新位置
        * 4. 绘制图像
        * 5. 2 3 4 2 3 4
        */
        let x = 0,
            y = 0,
            width = 100,
            height = 100;

        ctx.fillStyle = '#d6555f';
        ctx.fillRect(x, y, width, height);

        let speedX = 2,
            speedY = 2;

        setInterval(function () {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            x += speedX;
            if (x > canvas.width - width) {
                speedX *= -1;
            } else if (x < 0) {
                speedX *= -1;
            }

            y += speedY;
            if (y > canvas.height - height) {
                speedY *= -1;
            } else if (y < 0) {
                speedY *= -1;
            }

            ctx.fillRect(x, y, width, height);
        }, 30);
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

        // 请求关键帧运动
        ctx.beginPath();

        let x = 0,
            y = 0,
            width = 100,
            height = 100;

        ctx.fillStyle = '#d6555f';
        ctx.fillRect(x, y, width, height);

        let speedX = 2,
            speedY = 2;

        function move() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            x += speedX;
            if (x > canvas.width - width) {
                speedX *= -1;
            } else if (x < 0) {
                speedX *= -1;
            }

            y += speedY;
            if (y > canvas.height - height) {
                speedY *= -1;
            } else if (y < 0) {
                speedY *= -1;
            }

            ctx.fillRect(x, y, width, height);

            window.requestAnimationFrame(move);
        }
        move();
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');


        // 圆形碰撞反弹
        function Ball(x, y, r, speedX, speedY, color) {
            this.x = x;
            this.y = y;
            this.r = r;
            this.speedX = speedX;
            this.speedY =speedY;
            this.color = color;

            this.draw = function () {
                ctx.beginPath();
                ctx.fillStyle = this.color;
                ctx.arc(this.x, this.y, this.r, 0, Math.PI* 2);
                ctx.fill();
            }

            this.move = function () {
                this.x += this.speedX;
                if (this.x > canvas.width - this.r) {
                    this.speedX *= -1;
                } else if (this.x < this.r) {
                    this.speedX *= -1;
                }

                this.y += this.speedY;
                if (this.y > canvas.height - this.r) {
                    this.speedY *= -1;
                } else if (this.y < this.r) {
                    this.speedY *= -1;
                }
            }

        }

        let ball = new Ball(100, 100, 50, 2, 2, '#d6555f');

        ball.draw();

        function start() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ball.draw();
            ball.move();
            window.requestAnimationFrame(start);
        }
        start();
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');


        // 水平全景滚动
        var x = 0;

        function backgroundMove() {
            // 记录状态
            ctx.save();
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.translate(-x, 0);
            ctx.drawImage(bgImage, 0, 0);
            ctx.drawImage(bgImage, canvas.width, 0);

            // 判断x的偏移量
            x++;

            if (x >= canvas.width) {
                x = 0;
            }

            ctx.restore();
            window.requestAnimationFrame(backgroundMove);
        }

        let bgImage = new Image();
        bgImage.src = 'image.jpg';

        bgImage.onload = function () {
            backgroundMove();
        }
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');


        // save 和 restore
        ctx.beginPath();
        ctx.fillStyle = '#d6555f';
        ctx.save();
        ctx.fillRect(100, 100, 150, 150);
        ctx.closePath();

        ctx.beginPath();
        ctx.fillStyle = '#cce8cf';
        ctx.save();
        ctx.fillRect(100, 300, 150, 150);
        ctx.closePath();

        ctx.beginPath();
        ctx.restore();
        ctx.fillRect(350, 100, 150, 150);
        ctx.closePath();

        ctx.beginPath();
        ctx.restore();
        ctx.fillRect(350, 300, 150, 150);

        // 栈的存储方式
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');


        // 垂直全景移动
        var y = 0;
        function bgMove() {
            ctx.save();
            ctx.clearRect(0, 0, canvas.width,  canvas.height);
            ctx.translate(0, y);
            ctx.drawImage(bgImage, 0, 0);
            ctx.drawImage(bgImage, 0, canvas.height * -1);;
            y++;

            if (y >= canvas.height) {
                y = 0;
            }

            ctx.restore();
            window.requestAnimationFrame(bgMove);
        }

        var bgImage = new Image();
        bgImage.src = 'image.jpg';
        bgImage.onload = function () {
            bgMove();
        }
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');


        // 矩形的碰撞检测
        function Rect(x, y, width, height, color, speed) {
            this.x = x;
            this.y = y;
            this.width = width;
            this.height = height;
            this.color = color;
            this.speed = speed;
        }

        Rect.prototype.draw = function () {
            ctx.beginPath();
            ctx.fillStyle = this.color;
            ctx.fillRect(this.x, this.y, this.width, this.height);
            ctx.closePath();
        }

        Rect.prototype.move = function () {
            this.x += this.speed;

            if (this.x >= canvas.width - this.width) {
                this.speed *= -1;
            } else if (this.x < 0) {
                this.speed *= -1;
            }
        }

        let rect1 = new Rect(0, 100, 100, 100, '#d6555f', 2),
            rect2 = new Rect(700, 100, 100, 100, '#cce8cf', -2);

            rect1.draw();
            rect2.draw();

            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                rect1.draw();
                rect2.draw();
                rect1.move();
                rect2.move();

                // 检测
                if (isRectHit(rect1, rect2)) {
                    rect1.speed *= -1;
                    rect2.speed *= -1;
                }

                window.requestAnimationFrame(animate);
            }

            animate();

            function isRectHit(rect1, rect2) {
                // 获取矩形的最小x和最大x
                let min1 = rect1.x,
                    min2 = rect2.x,
                    max1 = rect1.x + rect1.width,
                    max2 = rect2.x + rect2.width;

                let min3 = Math.max(min1, min2),
                    max3 = Math.min(max1, max2);

                if (min3 < max3) {
                    return true;
                } else {
                    return false;
                }

            }
    }
}
```

```javascript
function draw() {
    var canvas = document.getElementById('canvas');

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');


        function Ball(x, y, r, color, speed) {
            this.x = x;
            this.y = y;
            this.r = r;
            this.color = color;
            this.speed = speed;
        }

        Ball.prototype.draw = function () {
            ctx.beginPath();
            ctx.fillStyle = this.color;
            ctx.arc(this.x, this.y, this.r, 0, Math.PI * 2);
            ctx.fill();
        }

        Ball.prototype.move = function () {
            this.x += this.speed;

            if (this.x > canvas.width - this.r) {
                this.speed *= -1;
            } else if (this.x < this.r) {
                this.speed *= -1;
            }
        }

        var ball1 = new Ball(50, 150, 50, '#d6555f', 5);
        var ball2 = new Ball(750, 150, 50, '#cce8cf', -2);

        ball1.draw();
        ball2.draw();

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            if (isCircleHit(ball1, ball2)) {
                ball1.speed *= -1;
                ball2.speed *= -1;
            }

            ball1.move();
            ball2.move();
            ball1.draw();
            ball2.draw();

            window.requestAnimationFrame(animate);
        }

        animate();

        function isCircleHit(ball1, ball2) {
            let x1 = ball1.x,
                y1 = ball1.y,
                r1 = ball1.r,
                x2 = ball2.x,
                y2 = ball2.y,
                r2 = ball2.r;

            let dx = x1 - x2,
                dy = y1 - y2;

            let distance = Math.sqrt(dx * dx + dy * dy);

            if (distance < r1 + r2) {
                return true;
            } else {
                return false;
            }
        }
    }
}
```

