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

               以下示範如何動態載入指定的component<br>
               <button @click="selectedComponent = 'appQuote'">Quote</button>
               <button @click="selectedComponent = 'appAuthor'">Author</button>
               <button @click="selectedComponent = 'appNew'">New</button>
               <p>{{ selectedComponent }}</p>
               <!-- 用 <component  v-bind:is=""> 來動態指定 component -->
               <!-- 透過 <keep-alive> 來避免因為動態切換 component 而導致已開啟的 component 被destroy 掉！ -->
               <keep-alive>
                    <component :is="selectedComponent">
                        <p>Default Content</p>
                    </component>
               </keep-alive>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteVue from '../components/Quote.vue'
    import AuthorVue from '../components/Author.vue'
    import NewVue from '../components/New.vue'

    export default {
        components: {
            appQuote: QuoteVue, // 或者寫成 app-quote: QuoteVue 也是可以的
            appAuthor: AuthorVue,
            appNew: NewVue
        },
        data: function() {
            return {
                titleString: 'Quote!!',
                selectedComponent: 'appQuote' //若要使用 data 紀錄 component 名稱，務必與所命名相同喔！
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
