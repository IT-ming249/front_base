
<template>
    <h1>选项式API</h1>
    <div>
        <button @click="onUpdateCount">选项式API计数：{{ count }}</button>
    </div>
</template>

<script >
//选项式API
export default{
    name: 'OptionsAPI',
    data(){
        return{
            count:0
        }
    },
    methods: {
        onUpdateCount(){
            this.count++;
        }
    }
}
</script>

<style scoped>
</style>
