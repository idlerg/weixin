
## 一、小程序开发和网页开发的区别

### 网页开发
- 1、网页开发中的额渲染线程和脚本线程是互斥的，长时间的脚本运行可能导致页面失去响应
- 2、网页开发者可以使用到各种浏览器暴露出来的DOM API和BOM API选中的操作
  
### 小程序开发
- 1、在小程序中，页面渲染和业务逻辑是分开的，分别运行在不同的线程中
逻辑层运行在JSCore中，并没有一个完整浏览器对象，因而缺少相关的DOM API和BOM API
因此非常熟悉的一些DOM操作的库，例如jQuery和Zepto等，在小程序中是无法运行的
同时JSCore的环境同NodeJS环境也是不完全相同的，所以一些NPM的包在小程序中也无法使用
- 2、小程序的性能介于 纯网页开发 与 原生 （native）开发之间

## 二、微信小程序开发UI组件库
- 1、weui-wxss
- 2、iview-weapp
- 3、vant-weapp
- 4、minui
- 5、wux-weapp
- 6、ColorUI（高颜值）

## 三、小程序目录结构
- 1、小程序主要包含1个描述真题程序的app和多个描述各自页面的app
- 2、app部分由3个文件组成，必须放在项目的根目录
- 3、
app.js（必须、小程序逻辑）
app.json(必须、全局配置)
app.wxss(非必须、全局公共样式表)
- 4、一个页面由4个文件组成（这4个文件必须具有相同的路劲和文件名）
文件类型
js：必须，页面逻辑
wxml：必须，页面结构
json：非必须，页面配置
wxss：非必须，页面样式表

## 四、微信小程序单位使用
rpx(responsive pixel):可以根据屏幕宽度进行自适应。规定屏幕宽为750rpx

## 五、小程序flex布局
开启了flex布局的元素叫flex container
flex container里面的元素叫做flex items
```
  /* 主轴方向 */
  /* flex-direction: column-reverse; */
  /* 主轴对齐方式 */
  /* justify-content: flex-end; */
  /* 单行还是多行显示 */
  /* flex-wrap: wrap; */
  /* 多行交叉轴对齐方式 */
  /* align-content: space-evenly; */
  /* 单行交叉轴对齐方式 */
  /* align-items: stretch; */
```
### 1、使用在flex container的CSS属性
> 一个设置主轴方向的属性，一个设置是否多行的属性，三个设置对齐方式的属性（一个主轴上的对齐方式，两个交叉轴上的对齐方式:一个单行的，一个多行的）

#### 属性display 
> 属性为flex 或者 inline-flex 可以成为flex container
- flex： flex container以block-level形式存在

#### 属性：flex-direction
> flex-direction决定了flex items 在 main axis排布的方向（此方向就是主轴的方向），有四个取值
- row：默认值,flex items默认都是沿着main axis（主轴）从main start开始往main end 方向排布
- row-reverse：相反的方向
- column:垂直显示
- column-reverse:垂直相反

#### 属性：justify-content
> justify-content决定了flex item 在 main axis 上的对齐方式

- flex-start：默认值，与 main start对齐
- flex-end：与 main end 对齐
- center：居中对齐
- space-between：flex items之间的距离相等，并与main start、main end 两端对齐
- space-around:flex items之间的距离相等，并与main start、main end之间的距离是flex items之间距离的一半
- space-evenly:flex items之间的距离相等，并与main start、main end之间的距离等于flex items之间的距离

#### 属性：align-items（用在单行的flex交叉轴的对齐布局）
> align-items决定了flex items在 cross axis（交叉轴）上的对齐方式
- stretch：默认值（拉伸），当flex items在cross axis方向的size 为 - auto 时，会自动拉伸至填充flex container
- flex-start:与cross start对齐
- flex-end:与corss end对齐
- center：居中对齐
- baseline：与基准线对齐（与使用的字体有关，字母的最低线就是基线，字体大小不同，但是字体在同一条线上）

#### 属性：align-content（用在多行的flex交叉轴的对齐布局）
> align-content决定了flex item 在 main axis 上的对齐方式
- flex-start：默认值，与 cross start对齐
- flex-end：与 cross end 对齐
- center：在交叉轴上居中对齐
- space-between：flex items之间的距离相等，并与cross start、cross end 两端对齐
- space-around:flex items之间的距离相等，并与 cross start、cross end之间的距离是flex items之间距离的一半
- space-evenly:flex items之间的距离相等，并与cross start、corss end之间的距离等于flex items之间的距离

#### 属性：flex-wrap
> flex-wrap决定flex items 单行还是多行
- nowrap:单行不换行
- wrap：换行，向 flex cross方向换行
- wrap-reverse：换行，flex cross 的cross start 和 cross end 方向相反

#### 属性：flex-flow
> flex-direction 和 flex-wrap的简写

>第一个属性值为flex-direction的属性值，第二个为属性值flex-wrap的属性值，也可以设置一个属性值

```
flex-flow: column wrap;
```

### 2、使用在flex items的CSS属性

#### 属性：flex
> flex 是 flex-grow 和 fles-shrin ? || flex-basis的简写 默认值是 flex：0 1 auto；


#### 属性：flex-grow
> 决定flex items 如何扩展

> - 当flex container在main axis方向上(宽度或者高度)有剩余size时，flex-grow属性才会有效
> - 如果所有flex items的flex-grow总和超sum过1,每个flex item扩展的size为flex container的剩余size * flex-grow/sum（扩展比列为flex-grow）
> - 如果所有的flex items 的flex-grow 总和不超过1,每个flex items扩展的size为flex container 的剩余size*flex-grow
> - felx-items 扩展后的最终size不能超过max-heigth/max-width


- 任意非负数字


#### 属性：flex-basis
> 用来设置flex items 在 main axis 方向上的base size，相当于 width， 只能用于 flex 布局，在flex布局中，flex相关属性优先级高

#### 属性：flex-shrink
> 决定flex items如何收缩

> - 当 flex items在main axis 方向上超过了 flex container的 size，flex-shrink属性才会有效
> - 当每个 flex items 的收缩 
> 收缩比例是 flex-shrink * item 的 width，收缩的比例为 收缩的距离 * 收缩的比例 / 收缩的总比例  

- 非负数字，默认值为1
  

#### 属性：order
> 决定了flex items的排布顺序，可以设置任意整数，越小就越排列在前面，默认值是0。默认值一样，则按照渲染顺序显示。
 - 正数
 - 负数
 - 0

#### 属性：align-self
> 重写align-items的样式，重写父类

- auto：默认值，继承父类
- stretch
- flex-start
- flex-end
- center
- baseline