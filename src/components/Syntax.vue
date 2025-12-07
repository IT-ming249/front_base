<script setup>
    import { ref, reactive } from 'vue';
    let username = ref("mmg")
    let code  = ref("<h1>hihi</h1>")
    let classname = 'bx'
    let age = 18
    let weather = ref("晴天")
    let count = ref(0)

    const onUpdateInfo = () =>(
        username.value = "mmh",
        weather.value = "雨天"
    )

    const books = reactive([
    {'title': '三国演义','author': '罗贯中'}, 
    {'title': '水浒传','author': '施耐庵'}, 
    {'title': '西游记','author': '吴承恩'}, 
    {'title': '红楼梦','author': '曹雪芹'}
    ])

    const book_names =  reactive(["红楼梦", "水浒传", "三国演义", "西游记"])

    //在script中定义与template中与ref同名的变量,必须同名
    let usernameInput = ref()

    const changeBooks = () => {
    book_names.sort(() => {
        return 5 - parseInt(Math.random() * 10)
    });
    }


    const person = reactive({
    "username": "嘿嘿",
    "age": 18,
    "homepage": "https://www.baidu.com/"
    })

    const onSplice = () =>{
    //splice(index,howmany,item1,...,itemX)：向数组中添加或者删除或者替换元素。
    // 下标从1开始添加元素
    book_names.splice(1,0,"金瓶梅")
    // 下标从0开始，删除2个元素
    book_names.splice(0,2)
    // 下标从0开始，替换2个元素
    book_names.splice(0,2,'金瓶梅','骆驼祥子')
    }

    const onSubtract = (sub_value, event) =>{
        count.value -= sub_value;
        console.log(event)
    }

    const gotoWebsite = function (event) {
    event.preventDefault(); //阻止默认行为
    window.location = "https://www.360.cn/"
    }

    const onShowUsername = () =>{
        //usernameInput.value标签对象，usernameInput.value.value才是用户输入的值
        console.log(usernameInput.value.value)
    }

</script>

<template>
    <h1>模板语法</h1>
    <h2>1. 分支语法</h2>
    <div>{{ username }}</div>
    <div>
        <button @click="onUpdateInfo">修改信息</button>
    </div>
    <div v-html="code"></div> <!-- 显示原生HTLML -->
    <div :class="classname">红色</div> <!-- 标签绑定变量 -->
    <div>{{ age>18? '去上网':'未成年' }}</div> <!-- JS表达式 -->

    <!--条件判断 符合条件的div会被渲染-->
    <div v-if="weather=='晴天'">出去玩</div>
    <div v-else-if="weather==下雨">宅家</div>
    <div v-else>啥都不干</div>
    
    <!-- v-show 总会被渲染，但可以指定显不显示， 需要频繁切换时用 -->
    <div v-show="true">这是v-show的div</div>
    
    <h2>2. 循环语法</h2>
    <h3>遍历数组</h3>
    <table>
        <thead>
        <tr>
            <th>索引</th>
            <th>书名</th>
            <th>作者</th>
        </tr>
        </thead>
        <tbody>
            <!-- (book, index) (元素，下标) 固定写法, 顺序别搞错了-->
            <tr v-for="(book, index) in books" :key="book.title">
                <td> {{ index +1  }}</td>
                <td> {{ book.title }}</td>
                <td> {{ book.author }}</td>
            </tr>
        </tbody>
    </table>

    <h3>遍历对象</h3>
    <p v-for="(value, key) in person" :key="key">键：{{key}}, 值：{{value}}</p>
    <h3>保持状态</h3>
    <!-- key不能重复，仅为int/str类型 不加key则标签不随数据的更改而更改-->
    <div v-for="book_name in book_names" :key="book_name">
        <label for="book">{{ book_name }}</label>
        <input type="text" v-bind:placeholder="book_name">
    </div>
    <button v-on:click="changeBooks">更换图书</button>

    <h2>3. 触发视图更新</h2>
    <!--splice(index,howmany,item1,...,itemX)：向数组中添加或者删除或者替换元素。-->
    <button @click="onSplice">更新书名列表</button>
    <!-- 经验：声明数组时用ref更好，方便覆盖-->

     <h2>4. 事件绑定</h2>
     <div>
        <p>count {{ count }}</p>
        <!--事件很短就可以直接写-->
        <button v-on:click="count++">添加count</button>
        <!--事件对象作为参数-->
        <button v-on:click="onSubtract(10, $event)">减10</button>
     </div>
     <div>
        <a href="https://www.baidu.com/" v-on:click="gotoWebsite($event)">百度</a>
     </div>
     <div>
        <!--使用默认修饰符  更多事件修饰符请参考：https://cn.vuejs.org/guide/essentials/event-handling.html-->
        <a href="https://www.baidu.com/" @click.prevent>360</a>
     </div>

     <h2>ref属性</h2>
     <!--ref属性用于在script 标签中获取template 中的元素。-->
     <!--在template中的某个标签上定义ref属性-->
     <input ref="usernameInput" placeholder="用户名">
     <button @click="onShowUsername">获取用户名</button>
</template>

<style scoped>
.bx{
    background-color: rgb(255, 0, 0);
}
</style>
