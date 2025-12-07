
<template>
    <h1>组合式API</h1>
    <div>
      <button @click="onUpdateCount">组合式API计数: {{ count }}</button>
    </div>
</template>
   
<!-- <script >
//组合式API (老式写法)
import {ref} from 'vue'
export default{
    name: 'CompsitionsAPI',
    setup(){
        let count = ref(0);
        function onUpdateCount(){
            count.value += 1;
        }

        return {
            count,
            onUpdateCount
        }
    }
}
</script> -->

<!-- <script>
// 采用选项式API的方式修改组合式API组件的名字
export default{
    name: "ComAPI"
}
</script> -->

<script setup name="ComAPI">
// 安装插件以后可以这样命名↑, 不设置的话组件名字跟vue文件名保持一致
// 使用setup不用再写setup和return了
import {ref} from 'vue'
let count = ref(0);

function onUpdateCount(){
    count.value += 1;
}
</script>

   
<style lang="">
</style>
   