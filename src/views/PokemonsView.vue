<script setup> 
    import { RouterLink } from 'vue-router';
    import { useGetData } from '@/composables/getData';

    const { data, getData, loading } = useGetData()

    getData('https://pokeapi.co/api/v2/pokemon/')
</script>

<template>
    <h1>Pokemons</h1>
    <p v-if="loading">Loading...</p>
    <div v-if="data">
        <ul class="list-group">
            <li
                v-for="pokemon in data.results"
                class="list-group-item"
            > 
                <router-link    
                    :to="`/pokemons/${pokemon.name}`" 
                    class="nav-link">
                    {{ pokemon.name[0].toUpperCase() + pokemon.name.slice(1) }}
                </router-link>
                
            </li>    
        </ul>
    </div>

</template>