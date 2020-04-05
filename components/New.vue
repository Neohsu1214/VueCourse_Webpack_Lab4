<template>
    <div>
        <h3>New Quote</h3>
        <!-- 用 counter 來驗證每次動態載入 component 時，是否會重新產生 component...預設是會 destroyed! -->

        <button @click="counter++">Increase!</button>
        <p>{{ counter }}</p>
    </div>    
</template>

<script>
export default {
    data: function() {
        return {
            counter: 0
        }
    },
    destroyed() {
        // 當被動態載入時，沒有被 <keep-alive> 包圍時，每次被切換掉都會被 destroy 掉！
        console.log('destroyed!');
    },
    deactivated() {
        // component在被切換離開前會執行 deactivated 並於切換回來時呼叫 activated
        console.log('Deactivated!');
    },
    activated() {
        // component在被切換離開前會執行 deactivated 並於切換回來時呼叫 activated
        console.log('Activated!');
    },
}
</script>

<style scoped>
   
</style>