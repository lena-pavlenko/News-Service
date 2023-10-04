<template>
    <header class="header">
        <nav class="light-blue darken-4">
            <div class="container">
                <div class="nav-wrapper row">
                    <div class="col">
                        <a href="/" class="brand-logo">News App</a>
                    </div>
                </div>
            </div>
        </nav>
    </header>
    <main class="main">
        <div class="search-controls">
            <div class="container">
                <div class="row">
                    <div class="col s12 m6">
                        <div class="card">
                            <form name="newsControls">
                                <div class="card-content">
                                    <span class="card-title">Search news</span>
                                    <div class="input-field">
                                        <input type="text" id="autocomplete-input" class="autocomplete" name="search" />
                                        <label for="autocomplete-input">Поиск по всем новостям</label>
                                    </div>
                                </div>
                                <div class="card-action">
                                    <button class="btn waves-effect waves-light light-blue darken-4" type="submit"
                                        name="action">
                                        Search
                                        <i class="material-icons right">search</i>
                                    </button>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="news-container">
            <div class="container">
                <article-list
                    :articles="articles"
                    v-if="!isPostLoading"
                />
                
                <div class="loading-banner" v-else>
                    <div class="lds-dual-ring"></div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
    import '@material-design-icons/font';
    import "materialize-css";
    import 'materialize-css/dist/css/materialize.min.css';
    import axios from 'axios'

    import ArticleList from '@/components/ArticleList'
    
    export default {
        components: {
            ArticleList
        },

        data() {
            return {
                articles: [],
                isPostLoading: false
            }
        },

        methods: {
            async getData() {
                try {
                    this.isPostLoading = true
                    const response = await axios.get(`https://newsapi.org/v2//top-headlines?country=us&category=entertainment&apiKey=YOURAPIKEY`)

                    if (Math.floor(response.status / 100) !== 2) {
                        console.log(`Error: Response status = ${response.status}`)
                        return
                    }
                    if (!response.data.articles.length) return
                    
                    this.articles = response.data.articles

                } catch (error) {
                    console.log(`Error: ${error}`)
                } finally {
                    this.isPostLoading = false
                }
            }
        },
        mounted() {
            M.AutoInit();

            this.getData()

            
        },
    }
</script>

<style lang="scss">
    .main {
        padding-top: 40px;
    }
    .news-container {
        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            grid-auto-flow: dense;
            row-gap: 20px;
        }

        .card {
            height: 100%;
            display: flex;
            flex-direction: column;

            &-content {
                flex-grow: 1;
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
    }

    .empty-text{
        font-size: 1.7rem;
        font-weight: 500;
        line-height: 1.2;
    }

    .loading-banner{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .lds-dual-ring {
        display: inline-block;
        width: 80px;
        height: 80px;

        &::after {
            content: " ";
            display: block;
            width: 64px;
            height: 64px;
            margin: 8px;
            border-radius: 50%;
            border: 6px solid #01579b;
            border-color: #01579b transparent #01579b transparent;
            animation: lds-dual-ring 1.2s linear infinite;
        }
    }
    @keyframes lds-dual-ring {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
    }
</style>
