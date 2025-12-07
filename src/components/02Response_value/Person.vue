<script setup>
import {ref} from "vue"
// ref函数，既可以定义基本数据类型的响应式变量，还可以定义复合的数据类型
let usename = ref("mmg")
let person = ref({
    usename: 'mmg',
    age: 18
})

const onUpdateUsername = () =>{
    //script中访问或修改响应式变量，需要通过 变量名.value的方式，而template中却不用
    usename.value = "mmh";
}

const onUpdateUserage = () =>{
    person.value.age++;
}

</script>

<template>
    <div>
        <h1>{{ usename }}</h1>
        <button @click="onUpdateUsername">点击修改用户名</button>
    </div>
    <div>
        <h1>年龄为{{ person.age}}</h1>
        <button @click="onUpdateUserage">点击修改年龄</button>
    </div>
</template>

<style scoped></style>
