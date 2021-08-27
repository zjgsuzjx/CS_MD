> 💥此MD/PDF/HTML文档由 [@竹梦者也 ](https://www.zjgsuzjx.top/)编辑制作，不可贩卖❌。仅供学习交流使用，下载后切勿随意传播。转载麻烦加上出处~
>
> 📌欢迎在留言区提供修改建议~
>
> 💌本文内容和代码来自于`张天禹`老师的`Vue2`教程
>
> 
>
> ✅2021.8.16	 @竹梦者也(https://www.zjgsuzjx.top) 









## 一、Vue核心

### 一、Vue简介

#### 1. 官网

Vue 2.x官网：https://cn.vuejs.org/

Vue 3.x官网：https://v3.cn.vuejs.org/

#### 2. 介绍

一套用于<u>构建用户界面</u>的<u>渐进式</u>JavaScript框架。

构建用户界面是指将数据转化为界面。渐进式是指从轻量小巧的核心库逐渐引用各式各样Vue插件。

**作者**为尤雨溪。

#### 3. 发展经历

<img src="https://img.zjgsuzjx.top/img/images/2021/07/19/b0263e0fea3c67e665fac184c869cba2.jpg" alt="b0263e0fea3c67e665fac184c869cba2.jpg" border="0" width="50%"/>

#### 4. 特点

- 采用组件化模式，提高代码复用率、且让代码更好维护。
- 声明式编码，让编码人员无需直接操作DOM，提高开发效率。（另外有命令式编码，类似面向过程）
- 使用虚拟DOM+优秀的Diff算法，尽量服用DOM节点。

### 二、初识Vue

#### 1. 安装

在目前阶段，可以先引入js文件来学习。

https://cn.vuejs.org/v2/guide/installation.html#%E7%9B%B4%E6%8E%A5%E7%94%A8-lt-script-gt-%E5%BC%95%E5%85%A5

下载**生产版本**。

然后需要下载浏览器插件（Vue专用的调试工具）。

https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd

用以下代码关闭浏览器提示：

```html
<script>
    Vue.config.productionTip = false
</script>
```

#### 2. 简单使用

```html
<div id="root">
    <h1>hello {{name}}</h1>
</div>

<script>
    Vue.config.productionTip = false
    // 创建Vue对象
    new Vue({
        el: '#root',  // el用于指定当前Vue实例为哪个容器服务，值通常是CSS选择器
        data: {  // data用于存储数据，数据供el所指定的容器去使用
            name: 'world'
        }
    });
</script>
```

**总结**：

1. 想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象；
2. root容器里的代码依然符合html规范，只不过混入了一些特殊的Vue语法；
3. root容器里的代码被称为**Vue模板**；

**注意**：

- Vue实例和容器是一一对应的。
- 真实开发中只有一个Vue实例，并且会配合着组件一起使用。
- {{xxx}}中的xxx要写js表达式，且xxx可以自动读取到data1中的所有属性。
- 一旦data中的数据发生改变，那么页面中用到该数据的地方也会自动更新。

### 三、模板语法

在容器中使用Vue专用的特殊语法。

#### 1. 插值语法

就是前面例子用到的写法。

**功能**：用于解析标签体内容。

**写法**：{{xxx}}，xxx是js表达式，且可以直接读取到data中的所有属性。

```html
<h1>hello {{name}}</h1>
```

#### 2. 指令语法

**功能**：用于解析标签（包括：标签属性、标签体内容、绑定事件等等）。

**举例**：`v-bind:href="xxx"` 或简写为 `:href="xxx"`，xxx同样要写js表达式，且可以直接读取到data中的所有属性。

**备注**：Vue中有很多的指令，且形式都是：`v-???`，此处我们只是拿`v-bind`举个例子。

```html
<div id="root">
    <a v-bind:href="address.url">{{address.age}}</a>
    <!-- 简写 -->
    <a :href="address.url">{{address.age}}</a>
</div>

<script>
    Vue.config.productionTip = false
    new Vue({
        el: '#root',
        data: {
            name: 'world',
            address:{ // 可以将冲突的名字放在对象里
                url:'www.zjgsuzjx.top',
                age:2
            }
        }
    });
</script>
```

### 四、数据绑定

可以分为单向数据绑定和双向数据绑定。

**单向数据绑定**

数据只能从data流向页面。使用`v-bind`

```html
<input type="text" v-bind:value="name"><br>
```

**双向数据绑定**

数据不仅能从data流向页面，还可以从页面流向data。使用`v-model`

```html
<input type="text" v-model:value="name"><br>
```

> 备注：
>
> 双向绑定一般都应用在**表单类元素**上（如：input、select等）
>
> `v-mode1:value`可以简写为`v-model`，因为`v-model`默认收集的就是value值。

如：

```html
<input type="text" v-model="name"><br>
```

### 五、番外1

el与data的两种写法

- el有两种写法：

（1）new Vue时配置el属性

（2）先创建Vue实例`vm`，随后再通过`vm.$mount('#root')`指定el的值。

- data有两种写法：

（1）对象式，就是上面的例子。

（2）函数式，如：

```js
data: function(){
    return {
        age:18
    }
}
```

> **如何选择**：目前哪种写法都可以，以后学习到组件时，data必须使用函数式，否则会报错。

> **注意**：由Vue管理的函数，一定不要写箭头函数，一旦写了箭头函数，this指向就不再是Vue实例了。

### 六、MVVM模型

- M：模型(Model) ：对应 data 中的数据
- V：视图(View) ：模板
- VM：视图模型(ViewModel) ： Vue 实例对象

<img src="https://img.zjgsuzjx.top/img/images/2021/07/19/8b4f019e9e5f79c609492caa9939bfa9.jpg" alt="8b4f019e9e5f79c609492caa9939bfa9.jpg" border="0" width="50%"/>

> `data`中所有的属性，最后都出现在了`vm`身上。因此`vm`身上所有的属性以及Vue原型上所有属性，在Vue模板中都可以直接使用。

### 七、数据代理

#### 1. 对象defineProperty方法

```js
let number = 18
let person={
    name:'张三'
}

Object.defineProperty(person,'age',{
    /*enumerable:true, // 控制属性是否可以被枚举
    writable:true, // 控制属性是否可以被修改
    configurable:true, // 控制属性是否可以被删除*/
    // 当读取age时，get函数会自动调用，且返回值就是age的值
    get(){
        console.log('读取age');
        return number
    },
    // 当修改age时，set函数会自动调用，且会修改age的值
    set(value){
        console.log('修改age');
        number=value
    }
})
```

#### 2. Vue中的数据代理

通过vm对象来代理data对象中属性的操作（读/写）

**好处**：更加方便的操作data中的数据

**基本原理**：通过`Object.defineProperty()`把data对象所有属性添加到vm上。为每一个添加到vm的属性都指定一个`getter/setter`。在`getter`和`setter`内部去操作（读/写）data中对应的属性。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/19/5792ecff6978bcc3897bb8a223125a7a.jpg" alt="5792ecff6978bcc3897bb8a223125a7a.jpg" border="0" width="70%"/>

例子：

```html
<div id="root">
    {{name}}-----{{age}}
</div>
<script>
    let vm=new Vue({
        el:"#root",
        data:{
            name:'张三',
            age:18
        }
    })
</script>
```

在控制台输入`vm.age=20`，则页面的age部分会发生修改，说明确实修改了data中的age。

### 八、事件处理

#### 1. 基本使用

```html
<div id="root">
    {{name}}-----{{age}}
    <button v-on:click="showInfo">点我</button>
    <!-- 简写 -->
    <!-- <button @click="showInfo">点我</button> -->
    <!-- 传参数 -->
    <button @click="showInfo2(666)">点我</button>
    <!-- 保留event -->
    <button @click="showInfo3(666,$event)">点我</button>
</div>
<script>
    let vm = new Vue({
        el: "#root",
        data: {
            name: '张三',
            age: 18
        },
        methods: {
            showInfo(event) {
                console.log(1);
            },
            showInfo2(number) {
                alert('zjgsuzjx', number)
            },
            showInfo3(number, event) {
                alert(number, event)
            }
        }
    })
</script>
```

事件的基本使用：

1.使用`v-on:xxx`或`@xxx`绑定事件，其中xxx是事件名；

2.事件的回调需要配置在`methods`对象中，最终会在vm上：

3.`methods`中配置的函数，不用箭头函数！否则this就不是vm了；

4.`methods`中配置的函数，都是被Vue所管理的函数，this的指向是vm或组件实例对象；

5.`@click="demo"`和`@click="demo($event)"`效果一致，但后者可以传参

> 注意：DOM元素要写在root容器里。

#### 2. 事件修饰符

```html
<div id="root">
    <!-- 阻止默认行为 -->
    <a href="https://www.zjgsuzjx.top" @click.prevent></a>
    <!-- 阻止事件冒泡 -->
    <div @click="showInfo">
        <div @click.stop="showInfo"></div>
    </div>
    <!-- 事件只触发一次 -->
    <a href="https://www.zjgsuzjx.top" @click.once></a>
</div>
```

其它（次要）：

`capture`：使用事件的捕获模式；

`self`：只有`event.target`是当前操作的元素时才触发事件；

`passive`：事件的默认行为立即执行，无需等待事件回调执行完毕；

> **补充说明**：`capture`是将冒泡触发的行为转为捕获触发行为。`self`的作用和`stop`差不多。`passive`通常用于移动端，例如鼠标滚轮时马上执行滚动行为，无需等待方法执行完毕。

**技巧**：如果要绑定多个事件，可以连写。如：`@click.stop.prevent`，意思为先停止冒泡再阻止默认行为。

#### 3. 键盘事件

```html
<div id="root">
    <input type="text" placeholder="按下回车输出内容" @keyup.enter="showInfo">
</div>
<script>
    let vm = new Vue({
        el: "#root",
        methods: {
            showInfo(e) {
                console.log(e.target.value);
            }
        }
    })
</script>
```

**Vue中常用的按键别名**：

- 回车=>enter
- 删除=>delete（捕获“删除”和“退格”键）
- 退出=>esc
- 空格=>space
- 换行=>tab（特殊，必须配合keydown去使用）
- 上=>up
- 下=>down
- 左=>left
- 右=>right

> **备注**：Vue未提供别名的按键，可以使用按键原始的key值去绑定，但注意要转为xxxxx-xxx（短横线命名）

系统修饰键（用法特殊）：`ctrl`、`alt`、`shift`、`win`

（1）配合keyup使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才被触发。

（2）配合keydouwn使用：正常触发事件。

> 不推荐使用keyCode去指定具体的按键，因为即将弃用。

`Vue.config.keycodes.自定义键名=键码`，可以去定制按键别名

**技巧**：如果要使用形如ctrl+v的键盘事件，也可以使用连写形式，如：`@keyup.ctrl.v`

### 九、计算属性

#### 1. 铺垫

在span标签里实时更新输入框的内容。用方法来实现。

```html
<div id="root">
    <input type="text" v-model="first"><br>
    <input type="text" v-model="last"><br>
    <!-- 可以在元素里面调方法 -->
    <span>{{fullname()}}</span>
</div>
<script>
    let vm = new Vue({
        el: "#root",
        data: {
            first: '张',
            last: '三'
        },
        methods: {
            fullname() {
                return this.first + '-' + this.last
            }
        }
    })
</script>
```

#### 2. 计算属性实际要用

**定义**：要用的属性不存在，要通过已有属性计算得来。

**原理**：底层借助了`Objcet.defineproperty`方法提供的`getter`和`setter`。

- get函数什么时候执行？

（1）初次读取时会执行一次。

（2）当<u>依赖</u>的数据发生改变时会被再次调用。

**优势**：与methods实现相比，内部有<u>缓存机制</u>（复用），效率更高，调试方便。

具体实现例子：

```html
<div id="root">
    姓：<input type="text" v-model="firstName">
    名：<input type="text" v-model="lastName">
    全名：<span>{{fullName}}</span>
</div>
<script type="text/javascript">
    const vm = new Vue({
        el: '#root',
        data: {
            firstName: '张',
            lastName: '三',
        },
        computed: {
            fullName: {
                //get有什么作用？当有人读取fullName时，get就会被调用，且返回值就作为fullName的值
                //get什么时候调用？1.初次读取fullName时。2.所依赖的数据发生变化时。
                get() {
                    console.log('get被调用了')
                    // console.log(this) //此处的this是vm
                    return this.firstName + '-' + this.lastName
                },
                //set什么时候调用? 当fullName被修改时。
                set(value) {
                    console.log('set', value)
                    const arr = value.split('-')
                    this.firstName = arr[0]
                    this.lastName = arr[1]
                }
            }
        }
    })
</script>
```

> 个人理解：计算属性是根据现有data中的属性进行计算后，再将其加入到data中的属性，所以**本质**还是属性，在DOM元素中不能写成方法。它随依赖的值变化而变化。计算属性中的this指向是Vue对象实例，因此可以很方便计算。

#### 3. 计算属性简写

**只读不改**时，即不需要`setter`时，才可以简写。

```js
computed: {
    fullName: {
        // 简写
        console.log('get被调用了')
        return this.firstName + '-' + this.lastName
    }
}
```

### 十、监视属性

#### 1. 基本用法

监视属性watch：使用`handler`方法

- 当被监视的属性**变化**时, 回调函数自动调用, 进行相关操作
- 监视的属性必须存在，才能进行监视！！

```html
<div id="root">
    <h2>{{info}}</h2>
    <button @click="change">切换天气</button>
</div>
<script>
    let vm = new Vue({
        el: "#root",
        data: {
            ishot: true
        },
        methods: {
            change() {
                this.ishot = !this.ishot
            }
        },
        computed:{
            info(){
                return this.ishot?'炎热':'凉爽'
            }
        },
        // (1).new Vue时传入watch配置
        watch:{
            ishot:{
                // immediate:true,  // 初始化时让handler调用一下
                handler(newValue,oldValue){
                    console.log('被调用了',newValue,oldValue);
                }
            }
        }
    })
</script>
```

第二种写法通过`vm.$watch`监视：

```js
vm.$watch('isHot',{
    // newValue时新属性，oldValue是旧属性
    handler(newValue,oldValue){
        console.log('isHot被修改了',newValue,oldValue)
    }
})
```

> 备注：要写在Vue实例对象外面。监视的属性可以是计算属性
>

> **注意**：在Vue控制台里，如果页面没有改变的属性，就算改变了属性的值，也不会在控制台里显示。

#### 2. 深度监视

Vue中的watch默认不监测对象内部值的改变（一层）。配置`deep:true`可以监测对象内部值改变（多层）。

```js
watch:{
    // 监视多级结构中某个属性的变化
    'numbers.a':{
        handler(){
            console.log('a被改变了')
        }
    }
    //监视多级结构中所有属性的变化
    numbers:{
        deep:true,  // 开启深度监视
        handler(){
            console.log('numbers改变了')
        }
    }
}
```

> **备注**：
>
> (1)Vue自身可以监测对象内部值的改变，但Vue提供的`watch`默认不可以！
>
> (2)使用`watch`时根据数据的具体结构，决定是否采用深度监视。

> **注意**：监视多级结构的某个属性要加**单引号**。

#### 3. 监视属性的简写

当配置项中不需要`deep`、`immediate`时，可以简写。

```js
watch:{
    //简写
    isHot(newValue,oldValue){
        console.log('isHot被修改了',newValue,oldValue,this)
    }
}
```

`vm.$watch`的简写形式：

```js
//简写
 vm.$watch('isHot', function(newValue , oldValue) {
    console.log('isHot被修改了',newValue,oldValue,this)
}) 
```

> 切记不要写成箭头函数。被Vue所管理的函数都不推荐写成箭头函数。
>

#### 4. 计算属性与监视属性

在某些场合下，可以用计算属性与监视属性来实现相同的效果。

如用wacth来实现修改姓名plus版案例：

```js
watch:{
    firstName(val){
        setTimeout(()=>{
            console.log(this)
            this.fullName = val + '-' + this.lastName
        },1000);
    },
    lastName(val){
        this.fullName = this.firstName + '-' + val
    }
}
```

> 请注意，这里的异步任务使用了箭头函数。如果不用箭头函数，`this`将执行异步任务的调用者，即`window`。

> 当有异步任务时，只能用`watch`，无法用计算属性实现。

**对比总结**：

- `computed`能完成的功能，`watch`都可以完成。
- `watch`能完成的功能，`computed`不一定能完成，例如：watch可以进行异步操作。

**备注**：

- 所有被Vue管理的函数，最好写成普通函数，这样`this`的指向才是vm 或 组件实例对象。

- 所有不被Vue所管理的函数（定时器的回调函数、ajax的回调函数等、Promise的回调函数），最好写成箭头函数，这样`this`的指向才是vm 或 组件实例对象。

### 十一、绑定样式

#### 1. class绑定样式

实现样式的切换和添加效果，使用`:class`。由Vue来管理这些样式。

```html
<div id="root">
    <!-- 绑定class样式--字符串写法，适用于：样式的类名不确定，需要动态指定 -->
    <div class="basic" :class="mood" @click="changeMood">{{name}}</div>
    <!-- 绑定class样式--数组写法，适用于：要绑定的样式个数不确定、名字也不确定 -->
    <div class="basic" :class="classArr">{{name}}</div>
    <!-- 绑定class样式--对象写法，适用于：要绑定的样式个数确定、名字也确定，但要动态决定用不用 -->
    <div class="basic" :class="classObj">{{name}}</div>
</div>
<script type="text/javascript">
    Vue.config.productionTip = false

    new Vue({
        el: '#root',
        data: {
            name: 'zjguszjx',
            mood: 'normal',
            classArr: ['zjguszjx1', 'zjguszjx2', 'zjguszjx3'],
            classObj: {
                atguigu1: false,
                atguigu2: false,
            }
        },
        methods: {
            changeMood() {
                const arr = ['happy', 'sad', 'normal']
                const index = Math.floor(Math.random() * 3)
                this.mood = arr[index]
            }
        },
    })
</script>
```

**总结**：

- **字符串**写法适用于：类名不确定，要动态获取。
- **对象**写法适用于：要绑定多个样式，个数不确定，名字也不确定。
- **数组**写法适用于：要绑定多个样式，个数确定，名字也确定，但不确定用不用。

#### 2. style绑定样式

```html
<div id="root">	
    <!-- 绑定style样式--对象写法 -->
    <div class="basic" :style="styleObj">{{name}}</div>
    <!-- 绑定style样式--数组写法 -->
    <div class="basic" :style="styleArr">{{name}}</div>
 </div>   
<script type="text/javascript">
    Vue.config.productionTip = false
    new Vue({
        el: '#root',
        data: {
            name: 'zjguszjx',
            styleObj: {
                // 这里要用特殊命名方式
                fontSize: '40px',
                color: 'red',
            },
            styleObj2: {
                backgroundColor: 'orange'
            },
            styleArr: [
                {
                    fontSize: '40px',
                    color: 'blue',
                },
                {
                    backgroundColor: 'gray'
                }
            ]
        },
    })
</script>
```

**备注**：

可以把样式属性写在元素里面，如`:style="{fontSize: xxx+'px'}"`其中`xxx`是动态值。

还可以写成`:style="[a,b]"`，其中`a`、`b`是样式对象。

### 十二、条件渲染

顾名思义，就是跟条件逻辑有关。这里主要讲`v-if`和`v-show`的用法。

**v-if**：

适用于：切换频率较低的场景。

特点：不展示的DOM元素<u>**直接被移除**</u>。

在引号内部可以写逻辑语句，最后的结果要求是布尔类型的值。

```html
<!-- 使用v-if做条件渲染 -->
<h2 v-if="false">欢迎来到{{name}}</h2>
<h2 v-if="1 === 1">欢迎来到{{name}}</h2>
```

另外可以配合`v-else`、`v-else-if`来使用。

```html
<!-- v-else和v-else-if -->
<div v-if="n === 1">Angular</div>
<div v-else-if="n === 2">React</div>
<div v-else-if="n === 3">Vue</div>
<div v-else>哈哈</div>
```

可以当作普通的`if...else if...else`结构来分析。

> **注意**：中间不能被打断，比如在`v-if`和`v-else`之间参杂了其它元素。

另外可以配合`template`来使用，最后template不会出现在页面结构上。

```html
<template v-if="n === 1">
    <h2>你好</h2>
    <h2>尚硅谷</h2>
    <h2>北京</h2>
</template>
```

**v-show**：

适用于：切换频率较高的场景。

特点：不展示的DOM元素未被移除，仅仅是使用样式<u>**隐藏**</u>掉。

```html
<!-- 使用v-show做条件渲染 -->
<h2 v-show="false">欢迎来到{{name}}</h2> 
<h2 v-show="1 === 1">欢迎来到{{name}}</h2> 
```

> **备注**：使用v-if的时，元素可能无法获取到，而使用v-show一定可以获取到。

### 十三、列表渲染

#### 1. v-for指令

用于展示列表数据。可遍历：数组、对象、字符串（用的很少）、指定次数（用的很少）

例子：

```html
<!-- 遍历数组 -->
<h2>人员列表（遍历数组）</h2>
<ul>
    <li v-for="(p,index) of persons" :key="index">
        {{p.name}}-{{p.age}}
    </li>
</ul>
```

> 注意：必须要由`:key`值，且是唯一。原因后续会提到。

其它例子：

```html
<!-- 遍历对象 -->
<h2>汽车信息（遍历对象）</h2>
<ul>
    <li v-for="(value,k) of car" :key="k">
        {{k}}-{{value}}
    </li>
</ul>

<!-- 遍历字符串 -->
<h2>测试遍历字符串（用得少）</h2>
<ul>
    <li v-for="(char,index) of str" :key="index">
        {{char}}-{{index}}
    </li>
</ul>
```

#### 2. key的原理

虚拟DOM中key的作用：key是虚拟DOM对象的标识，当数据发生变化时，Vue会根据**新数据**生成新的虚拟DOM, 随后Vue进行新虚拟DOM与旧虚拟DOM的差异比较。

**bad**：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/20/029c0c11f46cd856079f1f51ae327687.jpg" alt="029c0c11f46cd856079f1f51ae327687.jpg" border="0" width="90%"/>

缺点：若插入新元素时打乱顺序，则效率低下。

**good**：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/20/382491e9cb205dbfb7def456dbcbe2c0.jpg" alt="382491e9cb205dbfb7def456dbcbe2c0.jpg" border="0" width="90%"/>

优点：复用率高，提升效率。

> 对比算法就是diff算法，是Vue内部的处理算法。

**对比规则**：

- 旧虚拟DOM中找到了与新虚拟DOM相同的`key`：

若虚拟DOM中内容没变, 直接使用之前的真实DOM；若虚拟DOM中内容变了, 则生成新的真实DOM，随后替换掉页面中之前的真实DOM。

- 旧虚拟DOM中未找到与新虚拟DOM相同的`key`

创建新的真实DOM，随后渲染到到页面。

**用index作为key可能会引发的问题**：

- 若对数据进行逆序添加、逆序删除等**破坏顺序**操作，会产生没有必要的真实DOM更新，导致界面效果没问题, 但**效率低**。

- 如果结构中还包含输入类的DOM，如下：

```html
<li v-for="(p,index) of persons" :key="index">
    {{p.name}}-{{p.age}}
    <input type="text">
</li>
```

会产生错误DOM更新，导致界面有问题。

**开发中如何选择key**：

- 最好使用每条数据的唯一标识作为`key`, 比如id、手机号、身份证号、学号等唯一值。

- 如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，则使用index作为key是没有问题的。

#### 3. 列表过滤

实现模糊搜索效果。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/20/c4f7f364fae273a300032db94a093173.jpg" alt="c4f7f364fae273a300032db94a093173.jpg" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/07/20/c5d9079d8bfb185b3baeb4017833689d.jpg" alt="c5d9079d8bfb185b3baeb4017833689d.jpg" border="0" />

使用`watch`实现：

**容器内部**：

```html
<div id="root">
    <h2>人员列表</h2>
    <input type="text" placeholder="请输入名字" v-model="keyWord">
    <ul>
        <li v-for="(p,index) of filPerons" :key="index">
            {{p.name}}-{{p.age}}-{{p.sex}}
        </li>
    </ul>
</div>
```

**Vue实例对象内部**：

```js
data:{
    keyWord:'',
        persons:[
            {id:'001',name:'马冬梅',age:19,sex:'女'},
            {id:'002',name:'周冬雨',age:20,sex:'女'},
            {id:'003',name:'周杰伦',age:21,sex:'男'},
            {id:'004',name:'温兆伦',age:22,sex:'男'}
        ],
        filPerons:[]
},
watch:{
    keyWord:{
        // 先马上调用一次
        immediate:true,
        handler(val){
            this.filPerons = this.persons.filter((p)=>{
                return p.name.indexOf(val) !== -1
            })
        }
    }
}
```

> **注意**：`indexOf`函数对于空字符串即''，返回值依然是0。

用`computed`实现：

```js
computed:{
    filPerons(){
        return this.persons.filter((p)=>{
            return p.name.indexOf(this.keyWord) !== -1
        })
    }
}
```

> **备注**：`filter`内需要使用箭头函数，否则`this`指向会指向`window`。

> **总结**：`computed`要简单很多。

#### 4. 列表排序

实现点击按钮对查找后的元素进行排序，还可以复原位置。

将排序方法放到过滤语句的后面：

```js
computed: {
    filPerons() {
        const arr = this.persons.filter((p) => {
            return p.name.indexOf(this.keyWord) !== -1
        })
        //判断一下是否需要排序
        if (this.sortType) {
            arr.sort((p1, p2) => {
                return this.sortType === 1 ? p2.age - p1.age : p1.age - p2.age
            })
        }
        return arr
    }
}
```

> 通过改变计算属性来实现变化效果，从而不会影响原数据。这就是Vue的优势。
>

#### 5. Vue监视数据原理

以下代码模拟了Vue源码是怎么监视**对象**的：（响应式）

```js
// 创建一个监视的实例对象，用于监视data中属性的变化
const obs = new Observer(data)
console.log(obs)

// 准备一个vm实例对象
let vm = {}
vm._data = data = obs

// 构造函数
function Observer(obj){
    //汇总对象中所有的属性形成一个数组
    const keys = Object.keys(obj)
    //遍历
    keys.forEach((k)=>{
        Object.defineProperty(this,k,{
            get(){
                return obj[k]
            },
            set(val){
                console.log(`${k}被改了`)
                obj[k] = val
            }
        })
    })
}
```

> 真实的Vue源码要比这个完善很多，如可以通过`vm.属性名`来修改属性值，又或者可以为深层次的属性创建`get`和`set`方法。
>

以下代码演示了Vue如何给对象后天添加属性：

```js
<button @click="addSex">添加一个性别属性，默认值是男</button>

methods: {
    addSex(){
        // 下面两个方法都可以
        // Vue.set(this.student,'sex','男')
        this.$set(this.student,'sex','男')
    }
}
```

以下代码演示了Vue是怎么改变**数组元素**的：（响应式）

> **注意**：Vue没有为数组里的元素提供get和set，是用操作数组的方法。如push、pop、splice、shift、unshift、sort、reverse

在控制台输入：

```js
vm._data.student.hobby.push('学习')
// 也可以省去_data
vm.student.hobby.push('学习')
Vue.set(vm._data.student.hobby,1,'打台球')
// 也可以省去_data
Vue.set(vm.student.hobby,1,'打台球')
```

> Vue对数组的监视是通过对数组常用操作的包装来实现的。
>

**总结**

- vue会监视data中所有层次的数据。

- 通过`setter`实现监视，且要在`new Vue`时就传入要监测的数据。

(1) 对象中后追加的属性，Vue默认不做响应式处理

(2) 如需给后添加的属性做响应式，请使用如下API：

```js
Vue.set(target，propertyName/index，value)
// 或者
vm.$set(target，propertyName/index，value)
```

- 通过包裹数组更新元素的方法实现，本质就是做了两件事：

(1) 调用原生对应的方法对数组进行更新。

(2) 重新解析模板，进而更新页面。

- 在Vue修改数组中的某个元素一定要用如下方法

（1）使用这些API:`push()、pop()、shift()、unshift()、splice()、sort()、reverse()`

（2）`Vue.set()` 或 `vm.$set()`

> 特别注意：`Vue.set()` 和 `vm.$set()` 不能给vm 或 vm的**根数据对象**添加属性！！！

### 十四、收集表单数据

#### 1. 单选框

v-model收集的是value值，且要给标签配置value值。

如：

```html
<input type="radio" name="sex" v-model="userInfo.sex" value="male">
<input type="radio" name="sex" v-model="userInfo.sex" value="female">
```

#### 2. 多选框

- 如果没有配置input的value属性，那么收集的就是checked（勾选 or 未勾选，是布尔值）

如：

```html
<input type="checkbox" v-model="userInfo.hobby">
<input type="checkbox" v-model="userInfo.hobby">
```

- 配置input的value属性:


若v-model的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）

如：

```html
学习<input type="checkbox" v-model="userInfo.hobby" value="study">
打游戏<input type="checkbox" v-model="userInfo.hobby" value="game">
吃饭<input type="checkbox" v-model="userInfo.hobby" value="eat">

data:{
    userInfo:{
        hobby:''
    }
}
```

若v-model的初始值是数组，那么收集的的就是value组成的数组

如：

```html
学习<input type="checkbox" v-model="userInfo.hobby" value="study">
打游戏<input type="checkbox" v-model="userInfo.hobby" value="game">
吃饭<input type="checkbox" v-model="userInfo.hobby" value="eat">

data:{
    userInfo:{
        hobby:[]
    }
}
```

#### 3. v-model的三个修饰符

`lazy`：失去焦点再收集数据

`number`：输入字符串转为有效的数字

`trim`：输入首尾空格过滤

如：

```html
<textarea v-model.lazy="userInfo.other"></textarea> 
<input type="number" v-model.number="userInfo.age"> 
<input type="text" v-model.trim="userInfo.account">
```

### 十五、过滤器

定义：对要显示的数据进行特定格式化后再显示（适用于一些简单逻辑的处理）。

#### 1. 注册过滤器

第一种：

```js
//全局过滤器 
Vue.filter('mySlice',function(value){
    return value.slice(0,4)
})
```

全局过滤器必须要定义在`new Vue`之前。

第二种：

```js
//局部过滤器
new Vue({
    filters:{
        // 第二个是默认值，第一个参数必有
        timeFormater(value,str='YYYY年MM月DD日 HH:mm:ss'){
            // console.log('@',value)
            return dayjs(value).format(str)
        }
    }
})
```

> 注意：如果是局部过滤器的话，其它组件是用不了这个过滤器的。
>

#### 2. 使用过滤器

如：

```html
// 不写参数默认传入time
<h3>现在是：{{time | timeFormater}}</h3>
// 或用v-bind:属性
<h3 :x="msg | mySlice">zjgsuzjx</h3>
// 就算写了一个指定参数，time还是会被作为第一个参数传入方法形参
<h3>现在是：{{time | timeFormater('YYYY_MM_DD') | mySlice}}</h3>
```

**备注**：

- 过滤器也可以接收额外参数、多个过滤器也可以串联

- 过滤器并没有改变原本的数据, 是产生新的对应的数据

### 十六、其它内置指令

#### 1. v-text

作用：向其所在的节点中渲染文本内容。

```html
<div v-text="name"></div>
```

与插值语法的区别：`v-text`会替换掉节点中的内容，`{{xx}}`则不会。

#### 2. v-html

作用：向指定节点中渲染包含html结构的内容。

```html
<div v-html="str"></div>

<script type="text/javascript">
new Vue({
    el:'#root',
    data:{
        str:'<h3>你好啊！</h3>'
    }
})
</script>
```

与`v-text`的区别：`v-html`可以识别html结构

> **注意**：`v-html`有安全性问题，在网站上动态渲染任意HTML是非常危险的，容易导致XSS攻击。一定要在可信的内容上使用`v-html`，永不要用在用户提交的内容上！

#### 3. v-cloak

作用：解决网速过慢时，页面上出现未经Vue解析的模板。

本质是一个特殊属性，Vue实例创建完毕并接管容器后，会自动删掉`v-cloak`属性。

```html
<h2 v-cloak>{{name}}</h2>
```

使用css配合`v-cloak`可以解决网速慢时页面展示出`{{xxx}}`的问题。

```html
<style>
    [v-cloak]{
        display:none;
    }
</style>
```

#### 4. v-once

`v-once`所在节点在初次动态渲染后，就视为静态内容了。

```html
// 这里的{{n}}第一次解析之后，不会再变
<h2 v-once>初始化的n值是:{{n}}</h2>
```

以后数据的改变不会引起`v-once`所在结构的更新，可以用于优化性能。

#### 5. v-pre

作用：跳过其所在节点的编译过程。可利用它跳过没有使用指令语法、没有使用插值语法的节点，会加快编译。

```vue
<h2 v-pre>Vue其实很简单</h2>
// 这里的{{n}}不会被Vue解析
<h2 v-pre>当前的n值是:{{n}}</h2>
```

### 十七、自定义指令

顾名思义，将自己特殊的需求单独定义为一个指令。

#### 1. 简写形式

将自己自定义的指令放在Vue配置对象中，以方法的形式书写，方法名不需要写`v-xxx`，而是直接写`xxx`。

`element`是真实的DOM对象；`binding`是绑定时指令与DOM对象的关系。

> **备注**：将值插入到页面中必须要用`element.innerText`，而不能用`return`。

```js
new Vue({
    directives:{
        //big函数何时会被调用？1.指令与元素成功绑定时（一上来）。2.指令所在的模板被重新解析时。
        big(element,binding){
            console.log('big',this) //注意此处的this是window
            element.innerText = binding.value * 10
        }
    }
}
```

使用：

```html
<span v-big="n"></span>
```

> **注意**：在自定义的指令中，`this`的执行永远是`window`，因为需要用到`vm`对象里的值时，已经全部放在`value`里了。

#### 2. 完整形式

针对特殊的功能需求，如为input默认获取焦点，需要完整的自定义指令的方法。

Vue将其分为了三个阶段，分别是绑定时、插入元素时、更新元素时。

> **备注**：如同自动获取焦点和获取父元素等功能，都需要放在插入元素阶段才能奏效。

```js
new Vue({
    directives:{
        fbind:{
            //指令与元素成功绑定时（一上来）
            bind(element,binding){
                element.value = binding.value
            },
            //指令所在元素被插入页面时
            inserted(element,binding){
                element.focus()
            },
            //指令所在的模板被重新解析时
            update(element,binding){
                element.value = binding.value
            }
        }
    }
}
```

> **注意**：指令名如果是多个单词，要使用kebab-case命名方式，不要用camelCase命名。如`'big-number'(){}`，`v-big-number="n"`

#### 3. 全局与局部指令

**局部指令**就是如同上面的例子直接写到Vue配置对象中：

```js
new Vue({
    directives:{指令名:配置对象}
}
```

**全局指令**：

`Vue.directive(指令名,配置对象)` 或   `Vue.directive(指令名,回调函数)`

如：

```js
//定义全局指令
Vue.directive('fbind',{
    bind(element,binding){
        element.value = binding.value
    },
    inserted(element,binding){
        element.focus()
    },
    update(element,binding){
        element.value = binding.value
    }
})
```

### 十八、生命周期

**又名**：生命周期回调函数、生命周期函数、生命周期钩子。

**作用**：Vue在关键时刻帮我们调用的一些特殊名称的函数。

生命周期函数的名字不可更改，但函数的具体内容是程序员根据需求编写的。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/26/f6b5c0f65d0dbac2fd7922c37a72f0e0.png" alt="f6b5c0f65d0dbac2fd7922c37a72f0e0.png" border="0" />

> 注意：生命周期函数中的`this`指向是vm 或 组件实例对象。

常用的生命周期钩子：

`mounted`: 发送ajax请求、启动定时器、绑定自定义事件、订阅消息等【初始化操作】。

`beforeDestroy`: 清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】。

关于销毁Vue实例：

- 销毁后借助Vue开发者工具看不到任何信息。
- 销毁后自定义事件会失效，但原生DOM事件依然有效。
- 一般不会在`beforeDestroy`操作数据，因为即便操作数据，也不会再触发更新流程了。

例子：

```js
//.....
<h2 :style="{opacity}">欢迎学习Vue</h2>
// ......
new Vue({
    // ......
    //Vue完成模板的解析并把初始的真实DOM元素放入页面后（挂载完毕）调用mounted
    mounted(){
        this.timer = setInterval(() => {
            this.opacity -= 0.01
            if(this.opacity <= 0) this.opacity = 1
        },16)
    },
    beforeDestroy() {
        clearInterval(this.timer)
    },
})
```

**备注**：`template`也是一个配置对象。它会替换掉`<div id="root"></div>`全部内容，并且`id`将会消失。

```js
new Vue({
    el:'#root',
    template:`
       <div>
          <h2>当前的n值是：{{n}}</h2>
          <button @click="add">点我n+1</button>
       </div>
    `
})
```

## 二、组件化编程

> 组件就是一块砖，哪里需要哪里搬。
>

### 一、组件定义

#### 1. 组件是什么

用来实现局部(特定)功能效果的代码集合。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/27/8d85a18e68239c4d31b1622f73409b08.jpg" alt="8d85a18e68239c4d31b1622f73409b08.jpg" border="0" width="80%"/>

<img src="https://img.zjgsuzjx.top/img/images/2021/07/27/02fba60ec4a0a92b368e1801c48ef1da.jpg" alt="02fba60ec4a0a92b368e1801c48ef1da.jpg" border="0" />

#### 2. 作用

提高代码复用率，简化项目编码, 提高运行效率

#### 3. 组件化

当应用中的功能都是多组件的方式来编写的, 那这个应用就是一个组件化的应用。

### 二、非单文件组件

Vue中使用组件的三大步骤：定义组件(创建组件)、注册组件、使用组件(写组件标签)。

#### 1. 定义组件

使用`Vue.extend(options)`创建，其中`options`和`new Vue(options)`时传入的那个`options`几乎一样，但也有点区别。

```js
//第一步：创建school组件
 const school = Vue.extend({
     template:`
   <div class="demo">
      <h2>学校名称：{{schoolName}}</h2>
      <h2>学校地址：{{address}}</h2>
      <button @click="showName">点我提示学校名</button> 
   </div>
`,
     // el:'#root', //组件定义时，一定不要写el配置项，因为最终所有的组件都要被一个vm管理，由vm决定服务于哪个容器。
     data(){
         return {
             schoolName:'ZJGSU',
             address:'浙江杭州'
         }
     },
     methods: {
         showName(){
             alert(this.schoolName)
         }
     },
 })
```

> 备注：
>
> **data必须写成函数，为什么？**
>
> 避免组件被复用时，数据存在引用关系。
>
> **el不要写，为什么？**
>
> 最终所有的组件都要经过一个vm的管理，由vm中的el决定服务哪个容器。

#### 2. 注册组件

**局部注册**：靠`new Vue`的时候传入`components`选项

```js
//创建vm
new Vue({
    el:'#root',
    //第二步：注册组件（局部注册）
    components:{
        school,
        student
    }
})
```

**全局注册**：靠`Vue.component('组件名',组件)`

```js
//第二步：全局注册组件
Vue.component('hello',hello)
```

#### 3. 使用组件

```html
<!-- 准备好一个容器-->
<div id="root">
    <hello></hello>
    <!-- 第三步：编写组件标签 -->
    <school></school>
    <!-- 第三步：编写组件标签 -->
    <student></student>
</div>
```

同名组件的属性不会冲突，因为在定义时是return了一个对象。

#### 4. 注意事项

**关于组件名**

- 一个单词组成

第一种写法(首字母小写)：`school`

第二种写法(首字母大写)：`School`

- 多个单词组成

第一种写法(kebab-case命名)：`my-school`

第二种写法(CamelCase命名)：`MySchool` (需要Vue脚手架支持)

> **备注**：组件名尽可能回避HTML中已有的元素名称，例如：h2、H2都不行。

**关于组件标签**

第一种写法：`<school></school>`

第二种写法：`<school/>`

> **备注**：不用使用脚手架时，`<school/>`会导致后续组件不能渲染。

**一个简写方式**

`const school = Vue.extend(options)` 可简写为：`const school = options`，如：

```js
const s = {
     template:`
   // ...
`,
     data(){
         return {
             // ...
         }
     }
 }
```

> **备注**：可以使用`name`配置项指定组件在开发者工具中呈现的名字。

如：

```js
const s = {
     name:'zjgsuzjx',
     template:`
   // ...
`,
     data(){
         return {
             // ...
         }
     }
 }
```

#### 5. 组件嵌套

例子：让school里嵌套student，并且hello与school平级关系。

> 要注意被嵌套的组件使用的位置是在父级组件模板上。

```js
 //定义student组件
 const student = Vue.extend({
     name:'student',
     template:`
   <div>
      <h2>学生姓名：{{name}}</h2>
   </div>
`,
     data(){
         return {
             name:'zjguszjx'
         }
     }
 })

 //定义school组件
 const school = Vue.extend({
     name:'school',
     template:`
   <div>
      <h2>学校名称：{{name}}</h2>
      <student></student>
   </div>
`,
     data(){
         return {
             name:'ZJGSU'
         }
     },
     //注册组件（局部）
     components:{
         student
     }
 })

 //定义hello组件
 const hello = Vue.extend({
     template:`<h1>{{msg}}</h1>`,
     data(){
         return {
             msg:'hello world'
         }
     }
 })
```

> 在实际开发中，更常见的是vm会管理app组件，而app组件会控制所有组件。如同皇上、丞相、三省六部之间的关系。

```js
// 定义app组件
 const app = Vue.extend({
     template:`
   <div>
      <hello></hello>
      <school></school>
   </div>
`,
     components:{
         school,
         hello
     }
 })

// 创建vm
 new Vue({
     template:'<app></app>',
     el:'#root',
     //注册组件（局部）
     components:{app}
 })
```

#### 6. VueComponent

- 本质

组件**本质**是一个名为VueComponent的构造函数，且不是程序员定义的，是Vue.extend生成的。

我们只需要写`<school/>`或`<school></school>`，Vue解析时会帮我们创建school组件的实例对象，即Vue帮我们执行的：`new VueComponent(options)`。

> **注意**：每次调用`Vue.extend`，返回的都是一个**全新**的VueComponent

- 关于this指向

组件配置中：`data`函数、`methods`中的函数、`watch`中的函数、`computed`中的函数。它们的this均是**VueComponent实例对象**。

new Vue(options)配置中：data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是**Vue实例对象**。

> 备注：VueComponent的实例对象，以后简称`vc`（也可称之为：组件实例对象）。Vue的实例对象，以后简称`vm`。

#### 7. 内置关系（重要）

需要回顾原型链基础知识：https://www.zjgsuzjx.top/md/JavaScript%E9%AB%98%E7%BA%A7.html#8-%E5%8E%9F%E5%9E%8B%E9%93%BE

以及回顾成员查找机制：https://www.zjgsuzjx.top/md/JavaScript%E9%AB%98%E7%BA%A7.html#9-javascript-%E7%9A%84%E6%88%90%E5%91%98%E6%9F%A5%E6%89%BE%E6%9C%BA%E5%88%B6%E8%A7%84%E5%88%99

一个重要的内置关系：`VueComponent.prototype.__proto__ === Vue.prototype`

VueComponent和Vue之间**关系图**：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/27/3ac0764798b47ec0bd081797a038b2f2.jpg" alt="3ac0764798b47ec0bd081797a038b2f2.jpg" border="0" width="90%"/>

**作用**：让组件实例对象（vc）可以访问到 Vue原型上的属性、方法。

### 三、单文件组件

#### 1. 模板

```vue
<template>
  <!--写模板内容-->
</template>
<script>
    export default {
	// 写组件方法
    }
</script>
<style>
 /* 写样式 */
</style>
```

#### 2. 例子

**School.vue**

```vue
<template>
    <div class="demo">
        <h2>学校名称：{{name}}</h2>
        <h2>学校地址：{{address}}</h2>
        <button @click="showName">点我提示学校名</button>
    </div>
</template>
<script>
    // 最好用默认暴露
    export default {
        name:'School',
        data(){
            return {
                name:'尚硅谷',
                address:'北京昌平'
            }
        },
        methods: {
            showName(){
                alert(this.name)
            }
        },
    }
</script>
<style>
    .demo{
        background-color: orange;
    }
</style>
```

**App.vue**（用来汇总所有的组件）

```vue
<template>
<!-- 这里必须要加上div -->
    <div>
        <School></School>
        <Student></Student>
    </div>
</template>

<script>
    //引入组件
    import School from './School.vue'
    import Student from './Student.vue'

    export default {
        name:'App',
        components:{
            School,
            Student
        }
    }
</script>
```

**main.js**（引入App大组件，并创建Vue实例）

```js
// 整个项目的入口文件
import App from './App.vue'

new Vue({
    el:'#root',
    template:`<App></App>`,
    components:{App},
})
```

**index.html**：

```html
<div id="root"></div>
```

> **注意**：这样还不能执行代码，需要Vue脚手架。

## 三、Vue脚手架

### 一、初始化脚手架

#### 1. 脚手架概念

`CLI=command line interface`

Vue 脚手架是 Vue 官方提供的标准化开发工具（开发平台）。

官方中文文档: https://cli.vuejs.org/zh/

#### 2. 具体步骤

- 第一步（仅第一次执行）：全局安装@vue/cli。

`npm install -g @vue/cl`

- 第二步：切换到你要创建项目的目录，然后使用命令创建项目

`vue create xxxx`

- 第三步：到创建后所在文件夹启动项目（会自动编译）

`npm run serve`

三步全部完成后的样子：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/28/d59a78a0ca9c2ebd450d25af3b385bb3.jpg" alt="d59a78a0ca9c2ebd450d25af3b385bb3.jpg" border="0" />

#### 3. 模板目录分析

├── node_modules
├── public
│ ├── favicon.ico: 页签图标
│ └── index.html: 主页面
├── src
│ ├── assets: 存放静态资源
│ │ └── logo.png
│ │── component: 存放组件
│ │ └── HelloWorld.vue
│ │── App.vue: 汇总所有组件
│ │── main.js: 入口文件
├── .gitignore: git 版本管制忽略的配置
├── babel.config.js: babel 的配置文件
├── package.json: 应用包配置文件
├── README.md: 应用描述文件
├── package-lock.json：包版本控制文件

#### 4. render函数

render函数出现在main.js入口文件。

```js
import Vue from 'vue'
//创建Vue实例对象---vm
new Vue({
    el:'#app',
    //render函数完成了这个功能：将App组件放入容器中
    render: h => h(App),
})
```

完整版写法是：

```js
render(createElement){
    return createElement(App)
}
```

因为引入的并不是完整版的Vue，所以需要render作为模板解析器来解析。

**关于不同版本的Vue**：

- vue.js与vue.runtime.xxx.js的区别：

（1）vue.js是完整版的Vue，包含：核心功能+模板解析器。

（2）vue.runtime.xxx.js是运行版的Vue，只包含：核心功能；没有模板解析器。

> 因为vue.runtime.xxx.js没有模板解析器，所以不能使用`template`配置项，需要使用`render`函数接收到的`createElement`函数去指定具体内容。
>

### 二、关键属性

#### 1. 修改默认配置

新建一个`vue.config.js`文件，并且放在与`package.json`同级目录下。以下是部分被修改的配置：

```js
// commonJS模块化语法
module.exports = {
    pages:{
        index:{
            // 修改入口文件
            entry:'src/main.js',
        },
    },
    lintOnSave:false // 关闭语法检查
}
```

Vue脚手架隐藏了所有webpack相关的配置，若想查看具体的webpack 配置，请执行：`vue inspect > outp`

更多config文件个性化定制可见：https://cli.vuejs.org/zh/config/#vue-config-js

#### 2. ref属性

被用来给**元素**或**子组件**注册引用信息（`id`的替代者）

如：

```vue
<template>
    <div>
        <h1 v-text="msg" ref="title"></h1>
        <button ref="btn" @click="showDOM">点我输出上方的DOM元素</button>
        <School ref="sch"/>
    </div>
</template>

<script>
    export default {
        name:'App',
        methods: {
            showDOM(){
                console.log(this.$refs.title) //真实DOM元素
                console.log(this.$refs.btn) //真实DOM元素
                console.log(this.$refs.sch) //School组件的实例对象（vc）
            }
        },
    }
</script>
```

> 应用在html标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象（vc）

使用方式总结：

（1）打标识：```<h1 ref="xxx">.....</h1>``` 或 ```<School ref="xxx"></School>```

（2）获取：```this.$refs.xxx```

#### 3. props配置

**功能**：让组件接收外部传过来的数据，从而方便使用。

传递数据方式：

```vue
<div>
    <Student name="李四" sex="女" :age="18"/>
</div>
```

接收数据方式：

- 第一种方式（只接收）：

```js
//简单声明接收
props:['name','age','sex'] 
```

- 第二种方式（限制类型）：

```js
//接收的同时对数据进行类型限制
props:{
    name:String,
    age:Number,
    sex:String
}
```

- 第三种方式（限制类型、限制必要性、指定默认值）：

```js
//接收的同时对数据：进行类型限制+默认值的指定+必要性的限制
props:{
    name:{
        type:String, //name的类型是字符串
        required:true, //name是必要的
    },
    age:{
        type:Number,
        default:99 //默认值
    },
    sex:{
        type:String,
        required:true
    }
}
```

> **备注**：props是只读的，Vue底层会监测你对props的修改，如果进行了修改，就会发出<u>警告</u>，若业务需求确实需要修改，则需要复制props的内容到data中一份，然后去修改data中的数据。

如：

```vue
<template>
    <div>
        <h2>学生年龄：{{myAge+1}}</h2>
        <button @click="updateAge">尝试修改收到的年龄</button>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                // props的优先级比data要高，因此这里的myAge将会指向props的ages，不会被先解析
                myAge:this.age
            }
        },
        methods: {
            updateAge(){
                this.myAge++
            }
        },
        props:{
            age:{
                type:Number,
                default:99 //默认值
            }
        }
    }
</script>
```

#### 4. mixin混合

**功能**：可以把多个组件共用的配置提取成一个混入对象，如`data`、`methods`等等。

**使用方式**：

- 定义混合：

创建mixin.js文件，代码示例如下：

```js
// 分别暴露
export const hunhe = {
    methods: {
        showName(){
            alert(this.name)
        }
    },
    // 生命周期钩子
    mounted() {
        console.log('hello！')
    },
}
```

- 引入混入：


局部混入例子：（写在组件里）

```vue
<script>
    import {hunhe,hunhe2} from '../mixin'
    export default {
        name:'Student',
        data() {
            return {
                name:'张三',
                sex:'男'
            }
        },
        mixins:[hunhe,hunhe2]
    }
</script>
```

全局混入例子：（写在`main.js`里）

```js
import {hunhe} from './mixin'

Vue.mixin(hunhe)
```

> **备注**：混入的意思相当于并集，并不会替换到组件里的配置。

> **注意**：如果混入的配置属性和组件里的属性同名，则以组件为主，但是对于生命周期钩子，两者都会调用，而且组件定义的钩子后于混入的钩子被调用。

### 三、插件

**功能**：用于增强Vue，往Vue身上增加配置，之后可以在所有组件中可以全局使用这些配置。

**本质**：包含`install`方法的一个对象，`install`的第一个参数是`Vue`，第二个以后的参数是插件使用者传递的数据。

**定义插件**：创建`plugins.js`文件。

```js
export default {
    install(Vue){
        //全局过滤器
        Vue.filter('mySlice',function(value){
            return value.slice(0,4)
        })
        //定义全局指令
        Vue.directive('fbind',{
            update(element,binding){
                element.value = binding.value
            }
        })
        //定义混入
        Vue.mixin({
            // ...
        })
        //给Vue原型上添加一个方法（vm和vc就都能用了）
        Vue.prototype.hello = ()=>{alert('hello！')}
    }
}
```

**使用插件**：在`main.js`引入

```js
//引入插件
import plugins from './plugins'
//应用（使用）插件
Vue.use(plugins)
```

### 四、scoped样式

**作用**：让样式在局部生效，防止冲突。

**写法**：实例如下

```vue
<style scoped>
    .title{
        color: red;
    }
</style>
```

> **补充**：另外还有另外一种属性`lang`，是`language`的缩写。

如：

```vue
<style lang="less" scoped>
    .demo{
        background-color: pink;
        .zjgsu{
            font-size: 40px;
        }
    }
</style>
```

上面的`lang="less"`表示这个样式是less写法，默认是css写法。（不能直接编译，脚手架less版本有问题）

### 五、Todo-List案例

在学习下面小节之前，需要先学习制作该案例。https://www.bilibili.com/video/BV1Zy4y1K7SH?p=70（一直学习到P77）

#### 1. 本地存储

**含义**：将页面内产生的数据保存在浏览器中。存储内容大小一般支持5MB左右（不同浏览器可能还不一样）。分为`SessionStorage`和`LocalStorage`。

**方法**：

```js
xxxxxStorage.setItem('key', 'value'); // 该方法接受一个键和值作为参数，会把键值对添加到存储中，如果键名存在，则更新其对应的值。
xxxxxStorage.getItem('person'); // 该方法接受一个键名作为参数，返回键名对应的值。
xxxxxStorage.removeItem('key'); // 该方法接受一个键名作为参数，并把该键名从存储中删除。
xxxxxStorage.clear() // 该方法会清空存储中的所有数据。
```

**区别**：

`SessionStorage`存储的内容会随着浏览器窗口关闭而消失。

`LocalStorage`存储的内容，需要手动清除才会消失。

> **备注**：
>
> `xxxxxStorage.getItem(xxx)`如果xxx对应的value获取不到，那么`getItem`的返回值是`null`。
>
> `JSON.parse(null)`的结果依然是`null`。

#### 2. 组件的自定义事件

**含义**：一种<u>组件间通信</u>的方式，适用于：子组件 ===> 父组件。

**使用场景**：A是父组件，B是子组件，B想给A传数据，那么就要在A中给B绑定自定义事件（事件的回调在A中）。

**绑定自定义事件**：

- 第一种方式（在父组件中）


```vue
<Student @atguigu="getStudentName" @demo="m1"/>
// 或者
<Student v-on:atguigu="getStudentName" v-on:demo="m1"/>
```

- 第二种方式（在父组件中）


```vue
<Student ref="student"/>
<script>
// ... 
methods: {
    getSchoolName(name){
        console.log('App收到了学校名：',name)
    },
    // 也可以收到多个参数
    getStudentName(name,...params){
        console.log('App收到了学生名：',name,params)
    }
}
mounted() {
    this.$refs.student.$on('demo',this.getStudentName) //绑定自定义事件
}
</script>
```

**触发自定义事件**：

```vue
<template>
    <button @click="sendStudentlName">触发事件</button>
</template>
<script>
    // ...
    methods: {
        sendStudentlName(){
            this.$emit('demo')
            // 也可以传递多个参数
            this.$emit('demo',this.name,666,888,900)
        }
    }
    // ...
</script>
```

**解绑自定义事件**：

```js
this.$off('atguigu') //解绑一个自定义事件
this.$off(['atguigu','demo']) //解绑多个自定义事件
this.$off() //解绑所有的自定义事件
```

> **备注**：组件上也可以绑定原生DOM事件，需要使用```native```修饰符。

如：

```vue
<Student ref="student" @click.native="show"/>
```

> **注意**：也可以通过`this.$refs.xxx.$on('demo',回调)`绑定自定义事件。但是回调<span style="color:red">要么配置在methods中</span>，<span style="color:red">要么用箭头函数</span>，否则this指向会出问题！

#### 3. 全局事件总线（GlobalEventBus）

**作用**：一种组件间通信的方式，适用于<span style="color:red">任意组件间通信</span>。

**安装全局事件总线**：

```js
//创建vm
new Vue({
    el:'#app',
    render: h => h(App),
    beforeCreate() {
        Vue.prototype.$bus = this //安装全局事件总线
    },
})
```

> **备注**：为了能让所有的vc实例能够使用`$bus`，必须要将它绑定在Vue原型对象上面，原理是原型链的查找规则。这样在所有组件之间实现通信。

**使用事件总线**：

- 接收数据：A组件想接收数据，则在A组件中给`$bus`绑定自定义事件，事件的<span style="color:red">回调留在A组件自身。</span>

> 哪里接受数据，就在哪里绑定事件。

```js
mounted() {
    // console.log('School',this)
    this.$bus.$on('hello',(data)=>{
        console.log('我是School组件，收到了数据',data)
    })
},
// 在销毁之前需要用$off去解绑当前组件所用到的事件
beforeDestroy() {
    this.$bus.$off('hello')
}
```

- 提供数据：

```js
methods: {
    sendStudentName(){
        this.$bus.$emit('hello',this.name)
    }
}
```

#### 4. 消息订阅与发布（pubsub）

**作用**：一种组件间通信的方式，适用于<span style="color:red">任意组件间通信</span>。与全局事件总线的作用是一样的。

**使用步骤**：

- 需要安装pubsub：`npm i pubsub-js`

- 引入: `import pubsub from 'pubsub-js'`

- 接收数据（订阅）：A组件想接收数据，则在A组件中订阅消息，订阅的<span style="color:red">回调留在A组件自身。</span>

```js
mounted() {
    this.pubId = pubsub.subscribe('hello',(msgName,data)=>{
        console.log(data)
    })
}
```

> **注意**：`msgName`是订阅名，没有其它作用，第二个参数及以后才是传过来的数据。此外还必须写成箭头函数。

实际中可以这么写：（`_`表示占位）

```js
methods: {
    deleteTodo(_,id){
        this.todos = this.todos.filter( todo => todo.id !== id )
    }
}
mounted() {
    this.pubId = pubsub.subscribe('deleteTodo',this.deleteTodo)
}
```

- 提供数据：`pubsub.publish('xxx',数据)`

```js
export default {
    // ...
    methods: {
        sendStudentName() {
            pubsub.publish('hello', 666)
        }
    }
}
```

> **备注**：这种方式用来组件间通信使得很少，一是开发者工具不支持这种，二是全局事件总线也可以做到一样的功能。

#### 5. nextTick

**作用**：在下一次 DOM 更新结束后执行其指定的回调。适用于等模板解析完之后再执行函数内特定的功能的场合。

语法：`this.$nextTick(回调函数)`

比如：需要等`input`框被重新渲染在页面上后再自动获取焦点（如果没有这个函数则会导致`input`框没有出现就获取焦点从而报错）

```js
handleEdit(todo){
    if(todo.hasOwnProperty('isEdit')){
        todo.isEdit = true
    }else{
        this.$set(todo,'isEdit',true)
    }
    this.$nextTick(function(){
        this.$refs.inputTitle.focus()
    })
}
```

> 总结：当改变数据后，要基于更新后的新DOM进行某些操作时，要在`nextTick`所指定的回调函数中执行。
>

#### 6. 动画效果

**原理**：在插入、更新或移除 DOM元素时，在合适的时候给元素添加样式类名，从而达到动画的效果。

**使用active**：

```vue
<transition name="hello" appear>
    <h1 v-show="isShow">你好啊！</h1>
</transition>

<style>
    /* 进入过程中*/
    .hello-enter-active{
        animation: atguigu 0.5s linear;
    }
    /*离开过程中*/
    .hello-leave-active{
        animation: atguigu 0.5s linear reverse;
    }
</style>
```

> **备注**：`appear`表示页面一刷新就出现动画。使用```<transition>```包裹要过度的元素，并配置name属性。

**完整写法**：

```vue
// transition-group可以让里面元素有不同的动画效果，每个元素都要指定key值。
<transition-group name="hello" appear>
    <h1 v-show="!isShow" key="1">你好啊！</h1>
    <h1 v-show="isShow" key="2">尚硅谷！</h1>
</transition-group>
<style scoped>
	/* 进入的起点、离开的终点 */
	.hello-enter,.hello-leave-to{
		transform: translateX(-100%);
	}
	.hello-enter-active,.hello-leave-active{
		transition: 0.5s linear;
	}
	/* 进入的终点、离开的起点 */
	.hello-enter-to,.hello-leave{
		transform: translateX(0);
	}
</style>
```

**利用第三方动画库**：

网站指南：https://animate.style/

安装：`npm install animate.css`

引入：哪个组件用，在哪里引入

```js
import 'animate.css'
```

使用例子：

```vue
<transition-group
        appear
        name="animate__animated animate__bounce"
        enter-active-class="animate__swing"
        leave-active-class="animate__backOutUp"
>
    <h1 v-show="!isShow" key="1">你好啊！</h1>
    <h1 v-show="isShow" key="2">尚硅谷！</h1>
</transition-group>
```

## 四、Vue中的ajax

### 一、作用

主要是为了解决ajax请求的跨域问题，Vue脚手架有专门处理跨域请求的方法。

### 二、第一种配置方式

使用Vue-cli的devServer.proxy配置，详细见https://cli.vuejs.org/zh/config/#devserver-proxy

**原理**：利用cli搭建出一个微型的服务器代理（类似于Nginx），然后前端通过axios向cli搭建的服务器发送请求，该服务器再向真正需要请求的服务器发送请求。

**步骤**：

首先需要在`vue.config.js`里配置代理信息。

```js
module.exports = {
  devServer: {
    // 需要真正请求的服务器的地址，不需要后缀（基础路径）
    proxy: 'http://localhost:5000'
  }
}
```

然后在App组件里写以下代码：

```vue
<script>
    import axios from 'axios'
    export default {
        name: 'App',
        methods: {
            getStudents() {
                // 代理服务器的地址，要加上请求内容后缀
                axios.get('http://localhost:8080/students').then(
                    response => {
                        console.log('请求成功了', response.data)
                    },
                    error => {
                        console.log('请求失败了', error.message)
                    }
                )
            },
            getCars() {
                axios.get('http://localhost:8080/demo/cars').then(
                    // ........
                )
            }
        },
    }
</script>
```

**说明**：

1. 优点：配置简单，请求资源时直接发给前端（8080）即可。
2. 缺点：<u>不能配置多个代理</u>，不能灵活的控制请求是否走代理。
3. 工作方式：若按照上述配置代理，当请求了前端不存在的资源时，那么该请求会转发给服务器 （<u>优先匹配前端资源，就是public</u>）

### 三、第二种配置方式

首先需要在`vue.config.js`里配置代理信息。

```js
module.exports = {
  devServer: {
    proxy: {
      '/api': { // 匹配所有以 '/api1'开头的请求路径
        target: 'http://localhost:5000', // 代理目标的基础路径
        pathRewrite:{'^/atguigu':''},
       // ws: true, //用于支持websocket
       // changeOrigin: true //用于控制请求头中的host值
      },
      '/foo': {
        target: '<other_url>'
      }
    }
  }
}
/*
   changeOrigin设置为true时，服务器收到的请求头中的host为：localhost:5000
   changeOrigin设置为false时，服务器收到的请求头中的host为：localhost:8080
   changeOrigin默认值为true
*/
```

> **备注**：`pathRewrite`必写，否则会以为在服务器里找`/api`。

然后在App组件里写以下代码：

```vue
<script>
    import axios from 'axios'
    export default {
        name: 'App',
        methods: {
            getStudents() {
                // 代理服务器的地址，要加上请求内容后缀
                axios.get('http://localhost:8080/api/students').then(
                    response => {
                        console.log('请求成功了', response.data)
                    },
                    error => {
                        console.log('请求失败了', error.message)
                    }
                )
            },
            getCars() {
                axios.get('http://localhost:8080/demo/cars').then(
                    // ........
                )
            }
        },
    }
</script>
```

**说明**：

1. 优点：可以配置多个代理，且可以灵活的控制请求是否走代理。
2. 缺点：配置略微繁琐，请求资源时必须加前缀。

### 四、GitHub用户搜索案例

#### 1. 预习准备

复习知识点：https://es6.ruanyifeng.com/#docs/object#%E6%89%A9%E5%B1%95%E8%BF%90%E7%AE%97%E7%AC%A6

github官方搜索用户名的API接口：https://api.github.com/search/users?q=xxx

#### 2. 布局分析

图例如下：可以分为两个小组件。分别是Search组件和List组件。

- 搜索前：

<img src="https://img.zjgsuzjx.top/img/images/2021/08/07/d219b3abf8937598931859752a57dbb3.jpg" alt="d219b3abf8937598931859752a57dbb3.jpg" border="0" />

- 搜索后：

<img src="https://img.zjgsuzjx.top/img/images/2021/08/07/b29822d3990e336e761062b24d2595ae.jpg" alt="b29822d3990e336e761062b24d2595ae.jpg" border="0" />

#### 3. 程序设计

**List.vue**：

```vue
<template>
    <div class="row">
        <!-- 展示用户列表 -->
        <div v-show="info.users.length" class="card" v-for="user in info.users" :key="user.login">
            <a :href="user.html_url" target="_blank">
                <img :src="user.avatar_url" style='width: 100px'/>
            </a>
            <p class="card-text">{{user.login}}</p>
        </div>
        <!-- 展示欢迎词 -->
        <h1 v-show="info.isFirst">欢迎使用！</h1>
        <!-- 展示加载中 -->
        <h1 v-show="info.isLoading">加载中....</h1>
        <!-- 展示错误信息 -->
        <h1 v-show="info.errMsg">{{info.errMsg}}</h1>
    </div>
</template>
<script>
    export default {
        name:'List',
        data() {
            return {
                info:{
                    isFirst:true,
                    isLoading:false,
                    errMsg:'',
                    users:[]
                }
            }
        },
        mounted() {
            this.$bus.$on('updateListData',(dataObj)=>{
                // 扩展运算符
                this.info = {...this.info,...dataObj}
            })
        },
    }
</script>
```

> **备注**：设置`info`是为了使用扩展运算符

**Search.vue**：

```vue
<script>
    import axios from 'axios'
    export default {
        name:'Search',
        data() {
            return {
                keyWord:''
            }
        },
        methods: {
            searchUsers(){
                //请求前更新List的数据
                this.$bus.$emit('updateListData',{isLoading:true,errMsg:'',users:[],isFirst:false})
                axios.get(`https://api.github.com/search/users?q=${this.keyWord}`).then(
                    response => {
                        console.log('请求成功了')
                        //请求成功后更新List的数据
                        this.$bus.$emit('updateListData',{isLoading:false,errMsg:'',users:response.data.items})
                    },
                    error => {
                        //请求后更新List的数据
                        this.$bus.$emit('updateListData',{isLoading:false,errMsg:error.message,users:[]})
                    }
                )
            }
        },
    }
</script>
```

> **备注**：由于GitHub已经在开放的API上解决好了跨域问题，所以不需要单独设置。

#### 4. Vue-resource

Vue-resource是一个类似于axios的发送请求的插件，目前用的并不多。

**下载**：npm i vue-resource

**main.js中引入**：

```js
//引入插件
import vueResource from 'vue-resource'
//使用插件
Vue.use(vueResource)
```

剩下的只需要把`axios`换成`this.$http`就可以了。

### 五、插槽

**作用**：让父组件可以向子组件指定位置插入html结构，也是一种组件间通信的方式，适用于 **父组件 ===> 子组件** 。

**分类**：默认插槽、具名插槽、作用域插槽

#### 1. 默认插槽

```vue
<Category>
    <div>html结构1</div>
</Category>
```

> **备注**：模板解析完后再传过去的。也就是`style`放在这里也是能生效的。

```vue
<template>
    <div>
        <!-- 定义插槽 -->
        <slot>插槽默认内容...</slot>
    </div>
</template>
```

> **备注**：`slot`优先会调用组件内的内容，其次才是`slot`内的内容。

#### 2. 具名插槽

```vue
<Category title="美食" >
    <!-- V3已废弃，目前使用v-solt -->
    <img slot="center" src="https://s3.ax1x.com/2021/01/16/srJlq0.jpg" alt="">
    <a slot="footer" href="http://www.atguigu.com">更多美食</a>
</Category>
```

> **备注**：常用在组件需要多个插槽时，通过命名插槽的方式来指定对应部分。

```vue
<slot name="center">我是一些默认值，当使用者没有传递具体结构时，我会出现1</slot>
<slot name="footer">我是一些默认值，当使用者没有传递具体结构时，我会出现2</slot>
```

#### 3. 作用域插槽

```vue
<Category title="游戏">
    <template slot-scope="demo">
        <ul>
            <li v-for="(g,index) in demo.games" :key="index">{{g}}</li>
        </ul>
    </template>
</Category>
```

上面还有特殊写法：

```vue
<Category title="游戏">
    <!--解构赋值-->
    <template scope="{games}">
        <ol>
            <li v-for="(g,index) in games" :key="index">{{g}}</li>
        </ol>
    </template>
</Category>
```

category组件：

```vue
<div class="category">
    <!-- 传递数据-->
    <slot :games="games">我是默认的一些内容</slot>
</div>
```

> **备注**：由于数据全部放在组件里，因此在App.vue里使用数据时，并且有特殊的使用方法，将数据能够从组件传递到App。

## 五、vuex

### 一、基本概念

在Vue中实现**集中式**状态（**数据**）管理的一个**Vue插件**，对vue应用中多个组件的<u>共享状态</u>进行集中式的管理（读/写），也是一种组件间通信的方式，且适用于任意组件间通信。

> 用于多个组件需要共享数据时

### 二、工作原理

<img src="https://img.zjgsuzjx.top/img/images/2021/08/10/e6a6e835d98bdf88b2344e46b6aa19db.png" alt="e6a6e835d98bdf88b2344e46b6aa19db.png" border="0" width="70%"/>

**解释**：`state`会存储数据，当组件调用`dispatch`时，会触发一系列行为。首先是会经过`actions`，这个`actions`承担服务员的任务，会调用一些特殊的API。然后会经过`Mutations`，起到修改数据等具体数据的各种操作。然后传递给`State`真正会修改数据，最后会重新渲染页面。

**备注**：如果不发送ajax请求或需要判断的业务逻辑（如等一下时间再处理数据），也可以省略`actions`。

> **注意**：`Actions`、`Mutations`、`State`都是<u>对象数据类型</u>，都要经过`store`统一管理。因为诸如`dispatch`、`commit`方法都是由`store`提供的。所有的vc、vm对象都要能看到`store`！！

### 三、环境搭建

#### 1. 安装

因为是插件，所以需要下载vuex：`npm i vuex`

#### 2. 文件创建

创建文件：```src/store/index.js```

```js
//引入Vue核心库
import Vue from 'vue'
//引入Vuex
import Vuex from 'vuex'
//应用Vuex插件
Vue.use(Vuex)

//准备actions对象——响应组件中用户的动作
const actions = {}
//准备mutations对象——修改state中的数据
const mutations = {}
//准备state对象——保存具体的数据
const state = {}

//创建并暴露store
export default new Vuex.Store({
    actions,
    mutations,
    state
})
```

在```main.js```中创建vm时传入```store```配置项：

```js
......
//引入store
import store from './store'
......

//创建vm
new Vue({
    el:'#app',
    render: h => h(App),
    store
})
```

### 四、求和案例vuex版

**actions**：

> `context`可以译为上下文。

```js
const actions = {
    // 没有业务逻辑可以不这样写
    /* jia(context,value){
        console.log('actions中的jia被调用了')
        context.commit('JIA',value)
    },
    jian(context,value){
        console.log('actions中的jian被调用了')
        context.commit('JIAN',value)
    }, */
    // 业务逻辑必须写在actions里
    jiaOdd(context,value){
        console.log('actions中的jiaOdd被调用了')
        if(context.state.sum % 2){
            context.commit('JIA',value)
        }
    },
    jiaWait(context,value){
        console.log('actions中的jiaWait被调用了')
        setTimeout(()=>{
            context.commit('JIA',value)
        },500)
    }
}
```

> **备注**：如果由多个业务逻辑，还可以有以下写法：（类似链式）

```js
jiaOdd(context,value){
    context.dispatch('demo1',value)
    // 处理的逻辑1
},
demo1(context,value){
    context.dispatch('demo2',value)
     // 处理的逻辑2
},
demo2(context,value){
    if(context.state.sum % 2){
        context.commit('JIA',value)
    }
}
```

**mutations**：

```js
const mutations = {
    JIA(state,value){ // 最好是大写，做区分
        console.log('mutations中的JIA被调用了')
        state.sum += value
    },
    JIAN(state,value){
        console.log('mutations中的JIAN被调用了')
        state.sum -= value
    }
}
```

**state**：

```js
const state = {
    sum:0 //当前的和
}
```

**组件内**：

```js
export default {
    // .....
    methods: {
        increment(){
            // 没有业务逻辑可以直接跳过actions
            this.$store.commit('JIA',this.n)
        },
        decrement(){
            this.$store.commit('JIAN',this.n)
        },
        incrementOdd(){
            // 由业务逻辑不能跳过actions
            this.$store.dispatch('jiaOdd',this.n)
        },
        incrementWait(){
            this.$store.dispatch('jiaWait',this.n)
        },
    },
    // .....
}
```

### 五、vuex开发者调试工具

<img src="https://img.zjgsuzjx.top/img/images/2021/08/11/6e727117792e989df7c2f2b5c6c208f3.png" alt="6e727117792e989df7c2f2b5c6c208f3.png" border="0" />

### 六、getters配置

不是必须要使用的vuex配置。和计算属性有些像，为了不把运算放到插值语法中。

```js
//准备getters——用于将state中的数据进行加工
const getters = {
    bigSum(state){
        return state.sum*10
    }
}

// ....
<h3>当前求和放大10倍为：{{$store.getters.bigSum}}</h3>
```

### 七、四个map方法的使用

#### 1. mapState

用于帮助我们映射```state```中的数据为计算属性。可以帮助我们自动生成代码。

> **注意**：不能生成带有getters的代码。

首先需要在组件内引入：

```js
import {mapState} from 'vuex'
```

在组件内的计算属性内写：（注意要写在`computed`里。）

```js
computed: {
    //借助mapState生成计算属性：sum、school、subject（对象写法）
...mapState({sum:'sum',school:'school',subject:'subject'}),

    //借助mapState生成计算属性：sum、school、subject（数组写法）
...mapState(['sum','school','subject']),
},
```

> **备注**：...是解构赋值。如果借助于这种写法，开发者工具会专门有地方记录这些特殊的计算属性。

#### 2. mapGetters

专门生成带有`getters`的代码。用于帮助我们映射```getters```中的数据为计算属性。

注意要写在`computed`里。

```js
computed: {
    //借助mapGetters生成计算属性：bigSum（对象写法）
...mapGetters({bigSum:'bigSum'}),

    //借助mapGetters生成计算属性：bigSum（数组写法）
...mapGetters(['bigSum'])
}
```

#### 3. mapActions

用于帮助我们生成与```actions```对话的方法，即：包含```$store.dispatch(xxx)```的函数。

注意要写在`methods`里。

```js
methods:{
    //靠mapActions生成：incrementOdd、incrementWait（对象形式）
...mapActions({incrementOdd:'jiaOdd',incrementWait:'jiaWait'})

    //靠mapActions生成：incrementOdd、incrementWait（数组形式）
...mapActions(['jiaOdd','jiaWait'])
}
```

> 备注：需要传递参数需要：在模板中绑定事件时传递好参数，否则参数是事件对象。下面的`mapMutations`也是同理。
>

```html
<button @click="incrementOdd(n)">当前求和为奇数再加</button>
<button @click="incrementWait(n)">等一等再加</button>
```

#### 4. mapMutations

用于帮助我们生成与```mutations```对话的方法，即：包含```$store.commit(xxx)```的函数。

注意要写在`methods`里。

```js
methods:{
    //靠mapActions生成：increment、decrement（对象形式）
...mapMutations({increment:'JIA',decrement:'JIAN'}),

    //靠mapMutations生成：JIA、JIAN（对象形式）
...mapMutations(['JIA','JIAN']),
}
```

### 八、vuex模块化编码

#### 1. 概念

**目的**：让代码更好维护，让多种数据分类更加明确。

#### 2. 具体操作示例

首先需要修改`store.js`（即`store`文件夹下的`index.js`）

```js
const countAbout = {
    namespaced:true,//开启命名空间
    state:{x:1},
    mutations: { ... },
    actions: { ... },
    getters: {
        bigSum(state){
            return state.sum * 10
        }
    }
}

const personAbout = {
    namespaced:true,//开启命名空间
    state:{ ... },
    mutations: { ... },
    actions: { ... }
}

const store = new Vuex.Store({
    modules: {
        countAbout,
        personAbout
    }
})
```

> 进阶做法：将其按照模块拆分成不同的文件，最后在index.js汇总计课。

**模块1.js**：

```js
//求和相关的配置
export default {
    namespaced:true,
    actions:{
        // ...
    },
    mutations:{
        // ...
    },
    state:{
        // ...
    },
    getters:{
        // ...
    },
}
```

**模块2.js**：

```js
//人员管理相关的配置
export default {
    namespaced:true,
    actions:{
        // ...
    },
    mutations:{
        // ...
    },
    state:{
        // ...
    },
    getters:{
        // ...
    },
}
```

**index.js**：

```js
import Vue from 'vue'
//引入Vuex
import Vuex from 'vuex'
import countOptions from './count'
import personOptions from './person'
//应用Vuex插件
Vue.use(Vuex)

//创建并暴露store
export default new Vuex.Store({
    modules:{
        countAbout:countOptions,
        personAbout:personOptions
    }
})
```

开启命名空间后，组件中读取`state`数据：

```js
//方式一：自己直接读取
this.$store.state.personAbout.list
//方式二：借助mapState读取：
...mapState('countAbout',['sum','school','subject']),
```

开启命名空间后，组件中读取`getters`数据：

```js
//方式一：自己直接读取
this.$store.getters['personAbout/firstPersonName']
//方式二：借助mapGetters读取：
...mapGetters('countAbout',['bigSum'])
```

开启命名空间后，组件中调用`dispatch`：

```js
//方式一：自己直接dispatch
this.$store.dispatch('personAbout/addPersonWang',person)
//方式二：借助mapActions：
...mapActions('countAbout',{incrementOdd:'jiaOdd',incrementWait:'jiaWait'})
```

开启命名空间后，组件中调用`commit`：

```js
//方式一：自己直接commit
this.$store.commit('personAbout/ADD_PERSON',person)
//方式二：借助mapMutations：
...mapMutations('countAbout',{increment:'JIA',decrement:'JIAN'}),
```

> 所有的简写都是由代价的。-----张天禹老师
>

## 六、路由

### 一、概念

#### 1. 名称解析

**路由**： 一个路由（`route`）就是一组映射关系（`key - value`），多个路由需要路由器（`router`）进行管理。

**前端路由**：`key`是路径，`value`是组件。

**后端路由**：

**vue-router**：vue 的一个插件库，专门用来实现 SPA 应用。

#### 2. 对 SPA 应用的理解

1. 单页 Web 应用（single page web application，`SPA`）。
2.  整个应用只有一个完整的页面。
3. 点击页面中的导航链接不会刷新页面，只会做页面的局部更新。
4. 数据需要通过 ajax 请求获取。

### 二、基本使用

#### 1. 下载插件

安装vue-router：`npm i vue-router`

#### 2. 路由配置

引入插件：`import VueRouter from 'vue-router'`

应用插件：`Vue.use(VueRouter)`

编写`router`配置项：（设置`router`文件夹，创建**index.js**文件）

```js
// 该文件专门用于创建整个应用的路由器
import VueRouter from 'vue-router'
//引入组件
import About from '../components/About'
import Home from '../components/Home'

//创建并暴露一个路由器
export default new VueRouter({
    routes:[
        {
            path:'/about',
            component:About
        },
        {
            path:'/home',
            component:Home
        }
    ]
})
```

实现切换（`active-class`可配置高亮样式）：

```vue
<router-link class="list-group-item" active-class="active" to="/about">About</router-link>
 <router-link class="list-group-item" active-class="active" to="/home">Home</router-link>
```

> **备注**：`active-class`表示切换时，样式会转成这个类。

指定展示位置：

```vue
<router-view></router-view>
```

> **注意**：每个路由组件vc都有不同的`$route`和相同的`$router`

**其它注意点**：

1. 路由组件通常存放在```pages```文件夹，一般组件通常存放在```components```文件夹。
2. 通过切换，“隐藏”了的路由组件，默认是被销毁掉的，需要的时候再去挂载。
3. 每个组件都有自己的```$route```属性，里面存储着自己的路由信息。
4. 整个应用只有一个router，可以通过组件的```$router```属性获取到。

### 三、多级（嵌套）路由

配置路由规则，使用`children`配置项：

```js
//引入组件
//..........
//创建并暴露一个路由器
export default new VueRouter({
    routes:[
        {
            path:'/about',
            component:About
        },
        {
            path:'/home',
            component:Home,
            children:[
                {
                    // 注意不要加斜杆
                    path:'news',
                    component:News,
                },
                {
                    path:'message',
                    component:Message,
                }
            ]
        }
    ]
})
```

跳转（要写完整路径）：

```vue
<!--主要这里要写完整的相对路径-->
<router-link to="/home/news">News</router-link>
```

### 四、路由的query参数

传递参数：（这里用了三级嵌套路由的例子）

```vue
<!-- 跳转路由并携带query参数，to的字符串写法 -->
 <router-link :to="`/home/message/detail?id=${m.id}&title=${m.title}`">{{m.title}}</router-link>

<!-- 跳转路由并携带query参数，to的对象写法 -->
<router-link :to="{
path:'/home/message/detail',
    query:{
        id:m.id,
        title:m.title
     }
}">
     {{m.title}}
</router-link>
```

接收参数：

```vue
<li>消息编号：{{$route.query.id}}</li>
<li>消息标题：{{$route.query.title}}</li>
```

### 五、命名路由

**作用**：可以简化路由的跳转。

**使用**：

给路由命名：

```js
export default new VueRouter({
    routes: [
        {
            // 重新命名
            name: 'guanyu',
            path: '/about',
            component: About
        },
        {
            path: '/home',
            component: Home,
            children: [
                {
                    path: 'news',
                    component: News,
                },
                {
                    path: 'message',
                    component: Message,
                    children: [
                        {
                            // 重新命名
                            name: 'xiangqing',
                            path: 'detail',
                            component: Detail,
                        }
                    ]
                }
            ]
        }
    ]
})
```

简化跳转：

```vue
<!--简化前，需要写完整的路径 -->
<router-link to="/demo/test/welcome">跳转</router-link>

<!--简化后，直接通过名字跳转 -->
<router-link :to="{name:'hello'}">跳转</router-link>

<!--简化写法配合传递参数 -->
<router-link 
	:to="{
	name:'xiangqing',
	query:{
	    id:m.id,
	    title:m.title
	}
	}"
>跳转</router-link>
```

### 六、路由的params参数

配置路由，声明接收params参数：

```js
export default new VueRouter({
    routes: [
        {
            path: '/home',
            component: Home,
            children: [
                {
                    path: 'news',
                    component: News
                },
                {
                    component: Message,
                    children: [
                        {
                            name: 'xiangqing',
                            path: 'detail/:id/:title', //使用占位符声明接收params参数
                            component: Detail
                        }
                    ]
                }
            ]
        }
    ]
})
```

传递参数：

```vue
<!-- 跳转路由并携带params参数，to的字符串写法 -->
 <router-link :to="`/home/message/detail/${m.id}/${m.title}`">{{m.title}}</router-link>

<!-- 跳转路由并携带params参数，to的对象写法 -->
<router-link :to="{
               name:'xiangqing',
               params:{
                  id:m.id,
                  title:m.title
               }
            }">
    {{m.title}}
</router-link>
```

> **特别注意**：路由携带`params`参数时，若使用`to`的对象写法，则不能使用`path`配置项，必须使用`name`配置！

接收参数：

```html
<li>消息编号：{{$route.params.id}}</li>
<li>消息标题：{{$route.params.title}}</li>
```

### 七、路由的props配置

**作用**：让路由组件更方便的收到参数。适合于有较多参数传递的场合。

一共有三种写法：（全部配置在路由`index.js`中）

```js
{
    name:'xiangqing',
    path:'detail',
    component:Detail,
    //props的第一种写法，值为对象，该对象中的所有key-value都会以props的形式传给Detail组件。
    props:{a:1,b:'hello'}
}
```

> **备注**：这种用法用得比较少。

```js
{
    name:'xiangqing',
    path:'detail',
    component:Detail,
    //props的第二种写法，值为布尔值，若布尔值为真，就会把该路由组件收到的所有params参数，以props的形式传给Detail组件。
    props:true
}
```

> **注意**：这里只能接受到`params`参数，无法接收到`query`参数。

```js
{
    name:'xiangqing',
    path:'detail',
    component:Detail,
    //props的第三种写法，值为函数
    props($route){
        return {
            id:$route.query.id,
            title:$route.query.title,
            a:1,
            b:'hello'
        }
    }
}
```

> **备注**：用这种方法可以使用`query`参数。

随后在接收参数的那个路由组件配置如下：

```js
export default {
    name:'Detail',
    props:['id','title'],
}
```

### 八、router-link标签的replace属性

**作用**：控制路由跳转时操作浏览器历史记录的模式

浏览器的历史记录有两种写入方式：分别为`push`和`replace`，`push`是追加历史记录（类似于**栈**结构），`replace`是替换当前记录。路由跳转时候默认为`push`

如何开启`replace`模式：`<router-link replace .......>News</router-link>`

例子如下：

```vue
<router-link replace class="list-group-item" to="/about">About</router-link>
```

### 九、编程式路由导航

**作用**：不借助```<router-link> ```实现路由跳转，让路由跳转更加灵活。如在需要button跳转或自动跳转。

一共有以下的API：

```js
this.$router.push // 压栈
this.$router.replace // 替换
this.$router.forward() //前进
this.$router.back() //后退
this.$router.go(x) //可前进也可后退，x表示步数
```

例子：

```js
pushShow(m){
    this.$router.push({
        name:'xiangqing',
        query:{
            id:m.id,
            title:m.title
        }
    })
},
replaceShow(m){
    this.$router.replace({
        name:'xiangqing',
        query:{
            id:m.id,
            title:m.title
        }
    })
}
```

### 十、缓存路由组件

**作用**：为了能够切换导航栏之后，再切回来后数据还在。即让不展示的路由组件保持挂载，不被销毁。

> 注意是在展示区使用该方法。在哪里展示就在哪个路由里使用。

```vue
<!-- 缓存多个路由组件 -->
<keep-alive :include="['News','Message']">

<!-- 缓存一个路由组件 -->
<keep-alive include="News">
    <router-view></router-view>
</keep-alive>
```

> **注意**：如果没有include，则全部缓存，但没必要，必要的时候用。

### 十一、两个新的生命周期钩子

适合于比如需要使用缓冲但是又想要关掉定时器的场景。

**作用**：路由组件所独有的两个钩子，用于捕获路由组件的激活状态。

**具体名字**：

`activated`路由组件被激活时触发。

`deactivated`路由组件失活时触发。

**例子**：

```js
export default {
    // ....
    activated() {
        console.log('News组件被激活了')
        this.timer = setInterval(() => {
            // ....
        },16)
    },
    deactivated() {
        console.log('News组件失活了')
        // 清除定时器
        clearInterval(this.timer)
    },
}
```

### 十二、路由守卫

**作用**：对路由进行权限控制。简单来讲，就是在访问某个路由前需要对诸如身份信息进行判断，如果不满足条件则不允许访问。

**使用场景举例**：在访问个人中心的某几个模块前，需要校验身份信息是否正确。

**分类**：全局守卫、独享守卫、组件内守卫。

#### 1. 全局守卫

全局守卫分为全局前置守卫和全局后置守卫。分别用来充当<u>门卫</u>和<u>服务员</u>的功能。下面内容都写在路由的`index.js`配置中。

**全局前置守卫**：

```js
const router =  new VueRouter({
    // ......
    routes:[
        {
            name:'guanyu',
            path:'/about',
            component:About,
            // 这里是自定义属性
            meta:{isAuth:true,title:'关于'}
        }
    ]
})

//全局前置路由守卫————初始化的时候被调用、每次路由切换之前被调用
router.beforeEach((to,from,next)=>{
    console.log('前置路由守卫',to,from)
    if(to.meta.isAuth){ //判断是否需要鉴权
        if(localStorage.getItem('school')==='zjgsu'){
            next()
        }else{
            alert('学校名不对，无权限查看！')
        }
    }else{
        next()
    }
})

export default router
```

> **备注**：`meta{}`是路由元信息，可以用来自定义一些信息。

**全局后置守卫**：

```js
const router =  new VueRouter({
    // .......
})

//全局后置路由守卫————初始化的时候被调用、每次路由切换之后被调用
router.afterEach((to,from)=>{
    console.log('后置路由守卫',to,from)
    document.title = to.meta.title || 'zjgsu'
})

export default router
```

#### 2. 独享守卫

用于单个路由守卫配置。和全局守卫功能差不多。

下面内容都写在路由的`index.js`配置中。

```js
{
    name:'xinwen',
    path:'news',
    component:News,
    meta:{isAuth:true,title:'新闻'},
    beforeEnter: (to, from, next) => {
        console.log('独享路由守卫',to,from)
        if(to.meta.isAuth){ //判断是否需要鉴权
            if(localStorage.getItem('school')==='zjgsu'){
                next()
            }else{
                alert('学校名不对，无权限查看！')
            }
        }else{
            next()
        }
    }
}
```

> **注意**：没有`afterEnter`。

#### 3. 组件内守卫

每当从别的路由进来或从这个路由离开时才会生效。

下面内容都写在单个组件配置中。

```js
//通过路由规则，进入该组件时被调用
beforeRouteEnter (to, from, next) {
    console.log('About--beforeRouteEnter',to,from)
    if(to.meta.isAuth){ //判断是否需要鉴权
        if(localStorage.getItem('school')==='zjgsu'){
            next()
        }else{
            alert('学校名不对，无权限查看！')
        }
    }else{
        next()
    }
},

//通过路由规则，离开该组件时被调用
beforeRouteLeave (to, from, next) {
    console.log('About--beforeRouteLeave',to,from)
    next()
}
```

> **备注**：是通过路由进入和离开时才能生效，如果是直接进入或离开是不会生效的。

> **注意**：要注意调用时机顺序，比如`beforeRouteLeave`不适合放入更改网页标题等方法。

### 十三、路由器的两种工作模式

> 对于一个url来说，什么是hash值？—— #及其后面的内容就是hash值。

hash值不会包含在HTTP请求中，即hash值不会带给服务器。

**hash模式**：

1. 地址中永远带着`#`号，不美观。
2. 若以后将地址通过第三方手机app分享，若app校验严格，则地址会被标记为不合法。
3. 兼容性较好。

**history模式**：

1. 地址干净，美观。
2. 兼容性和hash模式相比略差。不加以特殊配置，可能会无法刷新访问。
3. 应用部署上线时需要后端人员支持，解决刷新页面服务端404的问题。如特殊的第三方包，或使用Nginx代理配置。

## 七、Vue UI 组件

### 一、移动端常用 UI 组件库

Vant https://youzan.github.io/vant（最常用）

Cube UI https://didi.github.io/cube-ui

Mint UI http://mint-ui.github.io

### 二、PC 端常用 UI 组件库

Element UI https://element.eleme.cn（最常用）

IView UI https://www.iviewui.co

全部引入时，会造成资源请求的文件体积太大了，需要按需引入。

举例：

```js
//完整引入
//引入ElementUI组件库
import ElementUI from 'element-ui';
//引入ElementUI全部样式
import 'element-ui/lib/theme-chalk/index.css';
//应用全部ElementUI
Vue.use(ElementUI);

//按需引入
import { Button,Row,DatePicker } from 'element-ui';
//按需应用ElementUI
Vue.component('zjx-button', Button);
Vue.component('zjx-row', Row);
Vue.component('zjx-date-picker', DatePicker);
```







