<template>
    <header class="header">
        <nav class="light-blue darken-4">
            <div class="container">
                <div class="nav-wrapper row">
                    <div class="col">
                        <a href="#" class="brand-logo">News App</a>
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
                                        <select name="country" id="country">
                                            <option value="us">United States</option>
                                            <option value="ru">Russia</option>
                                        </select>
                                        <label>Choose your country</label>
                                    </div>
                                    <div class="input-field">
                                        <select name="category" id="category">
                                            <option value="business">Business</option>
                                            <option value="entertainment">Entertainment</option>
                                            <option value="health">Health</option>
                                            <option value="science">Science</option>
                                            <option value="sports">Sports</option>
                                            <option value="technology">Technology</option>
                                        </select>
                                        <label>Choose category</label>
                                    </div>
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
                <div class="row grid-container">
                    <div class="col s12">
                        <div class="card">
                            <div class="card-top">
                                <div class="card-image">
                                    <img src="./assets/logo.png">
                                </div>
                                <span class="card-title">Card Title</span>
                            </div>
                            <div class="card-content">
                                <p>I am a very simple card. I am good at containing small bits of information.
                                    I am convenient because I require little markup to use effectively.
                                </p>
                            </div>
                            <div class="card-action">
                                <a href="#" class="light-blue-text text-darken-3">This is a link</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
    export default {

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
            &-image {
                width: clamp(150px, 300px, 100%);
                margin: 0 auto;
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
</style>
