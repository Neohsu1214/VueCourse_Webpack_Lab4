<template>
    <div>
        <!-- 使用 slot 來保留 parent component 定義好的 html 內容，此時 CSS也只會吃此 component 定義的 -->
        <slot></slot>
    </div>    
</template>

<script>
export default {
    
}
</script>

<style scoped>
    div {
        border: 1px solid #ccc;
        box-shadow: 1px 1px 2px black;
        padding: 30px;
        margin: 30px auto;
        text-align: center;
    }

    h2 {
        color: red;
    }
</style>