<template>
    <div class="row grid-container" v-if="articles.length">
        <article-item 
            v-for="article in articles"
            :article="article"
        />
    </div>
    <p class="empty-text center-align" v-else>Список статей пуст</p>
</template>

<script>
    import ArticleItem from '@/components/ArticleItem.vue';

    export default {
        components: {
            ArticleItem
        },
        props: {
            articles: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>