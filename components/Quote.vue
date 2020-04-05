<template>
    <div>
        <!-- 使用 slot 來保留 parent component 定義好的 html 內容，此時 CSS也只會吃此 component 定義的 -->
        <div class=title>
            <!-- 幫 slot 命名以做到不同內容塞到不同 slot 裡面去 -->
            <slot name="title"></slot>
            <!-- 當所命名的 slot 沒有被對應到的話，則會保留原本的內容 -->
            <span style="color: #ccc"><slot name="subtitle">The subtitle</slot></span>
        </div>
        <hr>
        <div>
            <!-- 幫 slot 命名以做到不同內容塞到不同 slot 裡面去 -->
            <slot name="content"></slot>
        </div>
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

    .title {
        font-style: italic;
    }
</style>