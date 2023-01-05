<script setup> 
    import axios from 'axios'
    import { ref } from 'vue';
    import { RouterLink } from 'vue-router';

    let pokemons = ref([])

    const getData = async() => {
        try {
            const {data} = await axios.get('https://pokeapi.co/api/v2/pokemon/')
            pokemons.value = data.results
        } catch (error) {
            console.log(error)
        }
    }

    getData()
</script>

<template>
    <h1>Pokemons</h1>
    <ul class="list-group">
        <li
            v-for="pokemon in pokemons"
            class="list-group-item"
        > 
            <router-link    
                :to="`/pokemons/${pokemon.name}`" 
                class="nav-link">
                {{ pokemon.name[0].toUpperCase() + pokemon.name.slice(1) }}
            </router-link>
            
        </li>    
    </ul>
</template>