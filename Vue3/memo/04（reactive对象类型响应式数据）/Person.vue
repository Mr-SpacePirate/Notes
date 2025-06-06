<template>
    <div class="person">
        <h2>汽车信息</h2>
        <h2>一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
        <button @click="changePrice">修改汽车价格</button>
        <button @click="changeCar">修改汽车数据</button>

        <br>

        <h2>游戏列表：</h2>
        <ul>
            <li v-for="game in games" :key="game.id">{{ game.name }}</li>
        </ul>
        <button @click="changeFirstGame">修改第一个游戏名字</button>
    </div>    
</template>

<!-- 配置组合式api -->
<script lang="ts" setup name="Person">
    import {reactive} from 'vue'

    let car = reactive({
        brand: '奔驰',
        price: 100
    })

    let games = reactive([
        {id: '01', name: '王者荣耀'},
        {id: '02', name: '原神'},
        {id: '03', name: '三国杀'}
    ])

    function changeFirstGame() {
        games[0].name = '吃鸡'
    }

    function changePrice() {
        car.price += 10
    }

    function changeCar() {
        Object.assign(car, {brand: '宝马', price: 1})   // ref可以直接赋值，reactive得用assign
    }
</script>

<style scoped>
    .person {
        background-color: skyblue;
        box-shadow: 0 0 10px;
        border-radius: 10px;
        padding: 20px;
    }
    button {
        margin: 0 5px;
    }
    li {
        font-size: 20px;
    }
</style>