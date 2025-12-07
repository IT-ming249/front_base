<script setup>
import { ref, reactive } from 'vue';
let username = ref("mmg")
let code  = ref("<h1>hihi</h1>")
let classname = 'bx'
let age = 18
let weather = ref("晴天")

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
</script>

<template>
    <h2>分支语法</h2>
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
    
    <h2>循环语法</h2>
    <table>
        <thead>
            <th>索引</th>
            <th>书名</th>
            <th>作者</th>
        </thead>
        <tbody>
            <!-- (book, index) (元素，下标) 固定写法-->
            <tr v-for="(book, index) in books" :key="book.title">
                <td> {{ index }}</td>
                <td> {{ book.title }}</td>
                <td> {{ book.author }}</td>
            </tr>
        </tbody>
    </table>

</template>

<style scoped>
.bx{
    background-color: rgb(255, 0, 0);
}
</style>
