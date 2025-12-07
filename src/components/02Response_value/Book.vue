<script setup>
import { reactive } from 'vue';
    let author = reactive ({
        username: "mmg",
        age: 20
    })

    let books  = reactive([
        {"name": "阿衰", "author": "猫小乐"}
    ])

    const onUpdateAuthor = () =>{
        // author.username = "mmh"
        //author = {'username': "jjj", age: 200}  这样会丢失响应式
        Object.assign(author, {'username': "jjj", age: 200}) //这样不丢响应式
    }

    const onUpdateBook = () =>{
        //books[0].author = "狗小哭"
        Object.assign(books, [{"name": "阿帅", "author": "狗小哭"}])
    }

</script>

<template>
<div>
    <h1>作者 {{author.username}} 年龄{{ author.age }}</h1>
    <button @click="onUpdateAuthor">更新作者</button>
</div>

<div>
    <h1>书籍{{ books[0].name }} 作者{{ books[0].author }}</h1>
    <button @click="onUpdateBook">更新书籍</button>
</div>
</template>

<style scoped></style>
