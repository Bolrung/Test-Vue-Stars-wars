<template>
    <div class=people>
        <Search @searchCharacter="searchCharacter"/>
        <ul v-for="i in this.characters" :key="i.name">
            <li><a href='#' v-on:click.stop.prevent="goToCharacterDetail(i.url)">{{i.name}}</a></li>
        </ul>
    </div>
</template>

<script>
import Search from "../components/Search.vue"
export default {
    name: 'people',
    components:{
        Search
    },
    props: {
        characters: Array,
    },
    data() {
        return {
            list_characters: []
        }
    },
    methods: {
        goToCharacterDetail(url) {
            this.$emit('characterDetail', url);
        },
        searchCharacter(input) {
            this.$emit('searchCharacter', input)
        }
    },
    created() {
        this.list_characters = this.characters
    }
}
</script>