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
                <a :href="article.url || ''" class="light-blue-text text-darken-3" target="_blank">Read more</a>
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
    .card {
        height: 100%;
        display: flex;
        flex-direction: column;

        &-content {
            flex-grow: 1;

            p{
                word-wrap: break-word;
            }
        }

        &-image {
            width: clamp(150px, 100%, 100%);
            aspect-ratio: 300/200;
            margin: 0 auto;

            img{
                height: 100%;
                object-fit: cover;
            }
        }

        &-title {
            background: rgb(1, 87, 155, 0.7);
            display: block;
            width: 100%;
            color: #fff;
            padding: 20px;
        }
    }
</style>