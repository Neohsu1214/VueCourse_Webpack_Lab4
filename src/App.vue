<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12">
               <app-quote>
                   <!-- 想將所定義的內容，原封不動地傳遞給 component 呈現？ 請用slot! -->
                   <!--<h2>Quote!</h2>-->
                   <!-- 幫 slot 命名以做到不同內容塞到不同 slot 裡面去 -->
                   <h2 slot="title">{{ titleString }}</h2>
                   <p slot="content">A wonderful quote!</p>
               </app-quote>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteVue from '../components/Quote.vue'

    export default {
        components: {
            appQuote: QuoteVue // 或者寫成 app-quote: QuoteVue 也是可以的
        },
        data: function() {
            return {
                titleString: 'Quote!!'
            }
        }
    }
</script>

<!-- 發現：這邊定義的CSS並不會影響到要傳給slot的內容 -->
<!-- slot特性：compile的結果 會吃 parent component定義的，style 會吃 child component 定義的 -->
<style scoped>
    h2 {
        color: blue;
    }
</style>
