<template>
    <div class="person">
        <h2>姓名：{{ name }}</h2>
        <h2>年龄：{{ age }}</h2>
        <button @click='showTel'>查看联系方式</button>
    </div>    
</template>

<script lang="ts">
    export default {
        name: 'Person',
        data() {
            return {
                name: '张三',
                age: 18,
                tel: '13125498045'
            }
        },
        methods: {
            showTel() {
                alert(this.tel)
            }
        }
    }
</script>

<style scoped>
    .person {
        background-color: skyblue;
        box-shadow: 0 0 10px;
        border-radius: 10px;
        padding: 20px;
    }
</style>