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
                            <search-form
                                @search="searchNews"
                            />
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
    import SearchForm from '@/components/SearchForm';
    
    export default {
        components: {
            ArticleList,
            SearchForm
        },

        data() {
            return {
                articles: [],
                isPostLoading: false,
            }
        },

        methods: {
            async getNews(isSearching = false, query = '') {
                let response = {}
                try {
                    this.isPostLoading = true
                    if (!isSearching) {
                        response = await axios.get(`https://newsapi.org/v2/top-headlines?country=ru&apiKey=YOUR_API_KEY`)
                    } else {
                        if (query === '') {
                            this.showMessage('Введите что-нибудь', 'error-msg')
                            return
                        }
                        response = await axios.get(`https://newsapi.org/v2/everything?q=${query}&apiKey=YOUR_API_KEY`)
                    }
                    
                    if (Math.floor(response.status / 100) !== 2) {
                        console.log(`Error: Response status = ${response.status}`)
                        return
                    }
                    if (!response.data.articles.length) {
                        this.showMessage('Ничего не найдено', 'msg-error')
                        return
                    }
                    
                    this.articles = response.data.articles

                } catch (error) {
                    console.log(`Error: ${error}`)
                    this.showMessage('Возникла ошибка', 'msg-error')
                } finally {
                    this.isPostLoading = false
                }
            },

            showMessage(msg, type = 'success') {
                M.toast(
                    {
                        html: msg,
                        classes: type
                    }
                )
            },

            searchNews(searchQuery) {
                this.getNews(true, searchQuery)
            },
        },
        mounted() {
            M.AutoInit();

            this.getNews()
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
