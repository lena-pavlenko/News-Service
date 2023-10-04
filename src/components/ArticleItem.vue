<template>
    <div class="col s12">
        <div class="card">
            <div class="card-top">
                <div class="card-image">
                    <img :src="article.urlToImage || '/assets/default-pic.jpg'">
                </div>
                <span class="card-title">{{ article.title || 'No title' }}</span>
            </div>
            <div class="card-content">
                <p>{{ article.description || 'No description' }}</p>
            </div>
            <div class="card-action">
                <a :href="article.url || ''" class="light-blue-text text-darken-3">This is a link</a>
            </div>
        </div>
    </div>
    
</template>

<script>
    export default {
        props: {
            article: {
                type: Object,
                required: true
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>