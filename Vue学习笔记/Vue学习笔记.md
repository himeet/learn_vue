## 1. 查看版本信息

```
npm --version  // 查看npm版本
```

```
node --version  // 查看node版本
```

## 2. 安装vue-cli工具

```
// 全局安装vue-cli 2
npm i -g vue-cli    // i代表install -g代表全局安装   安装vue-cli 2

// 全局安装vue-cli 3/4
npm install -g @vue/cli   // 安装vue-cli 3/4

// 卸载vue-cli 2再安装vue-cli 3/4
npm uninstall vue-cli -g  // 卸载vue-cli 2
npm cache clean --force   // 清除缓存
npm install -g @vue/cli  // 安装vue-cli 3/4
```

## 3.Vue页面上的绑定

```
<button type="button" v-on:click="submit()"></button>  // 为button绑定一个click事件，click事件触发后执行submit()函数
```

```
<a v-bind:href="url"></a>   // 为<a>绑定一个变量href，href的值为变量url。等价于<a :href="url"></a>
```

```
/**
* 创建Vue对象，添加数据和方法
**/
<script>
        new Vue({
            el: '#app',
            data: {
                msg: 'hello vue!',
                count: 0,
                template: '<div>hello template</div>',
                url:'http://www.baidu.com'
            },
            methods: {
                submit: function () {
                    this.count++;
                }
            }
        })
    </script>
```

## 4.监听器(watch)与计算属性(computed)

```
<script>
    var arr = 'arr_test'
    var app = new Vue({
                el: "#app",
                data: {
                    msg: "Hello Vue!",
                    another: "another"
                },
                watch: {
                    msg: function(newval, oldval) {  // watch只对监听的一个变量msg有效
                        console.log('newval is: ' + newval)
                        console.log('oldval is: ' + oldval)
                    }
                },
                computed: {
                    msg1: function() {
                        return 'computed:' + this.msg + this.another + arr // computed可以获得多个变量的变化
                    }
                }
            })
</script>
```

watch使用场景：异步场景

computed使用场景：数据联动

## 5. 条件渲染、列表渲染、Class与Style绑定

```
/**
* 条件渲染
**/
<div v-if="count > 0">
判断1：count大于0，count的值为：{{count}}
</div>
<div v-else-if="count == 0">
判断2：count等于0，count的值为：{{count}}
</div>
<div v-else>
判断3：count小于0，count的值为：{{count}}
</div>
<div v-show="count == -1">当show等于{{count}}才显示--->show:{{count}}</div>
```

```
/**
* 列表渲染
**/
<body>
    <div id="app">
        <div v-for = "item in list">{{item}}</div>
        <div v-for = "person in p_list">{{person}}</div>
        <div v-for = "person in p_list">{{person.name}}---->{{person.age}}</div>
    </div>

    <script>
        var app = new Vue({
            el: "#app",
            data: {
                msg: "Hello Vue!",
                list: [1,2,3,4,5,6,7,8,9,10],
                p_list: [{  // 对象数组
                    name: 'Mike',
                    age: 29
                }, {
                    name: 'Lusy',
                    age: 18
                }, {
                    name: 'Trump',
                    age: 56
                }]
            }
        })
    </script>
</body>
```

```
/**
* Class的绑定和CSS Style的绑定
**/
<body>
    <div id="app">
        <div v-for = "item in list">{{item}}</div>
        <div v-for = "person in p_list">{{person}}</div>
        <div v-for = "person in p_list"
        <!--  或者写成v-bind:class="{['active', 'add', 'more']}" -->
        <!--  或者写成v-bind:class="{'active': true}" -->
             v-bind:class="['active', 'add', 'more', {'another': 'true'}]"
             v-bind:style="styleMsg">
            {{person.name}}---->{{person.age}}
        </div>
    </div>

    <script>
        var app = new Vue({
            el: "#app",
            data: {
                msg: "Hello Vue!",
                list: [1,2,3,4,5,6,7,8,9,10],
                p_list: [{  // 对象数组
                    name: 'Mike',
                    age: 29
                }, {
                    name: 'Lusy',
                    age: 18
                }, {
                    name: 'Trump',
                    age: 56
                }],
                styleMsg: {  // v-bind绑定css样式
                    color: 'red',
                    textShadow: '0 0 5px green'
                }
            }
        })
    </script>
</body>
```

## 6.Vue创建项目(基于vue-cli 3)

进入到项目文件夹下

```
vue create hello-world
```





