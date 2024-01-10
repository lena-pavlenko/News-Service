<template>
    <form name="newsControls">
        <div class="card-content">
            <span class="card-title">Search news</span>
            <div class="input-field">
                <input 
                    type="text" 
                    id="autocomplete-input" 
                    class="autocomplete" 
                    name="search"
                    v-model="searchQuery"
                />
                <label for="autocomplete-input">Поиск по всем новостям</label>
            </div>
        </div>
        <div class="card-action">
            <button 
                class="btn waves-effect waves-light light-blue darken-4" 
                name="action"
                @click.prevent="$emit('search', searchQuery)" 
            >
                Search
                <i class="material-icons right">search</i>
            </button>
        </div>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                searchQuery: ''
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>