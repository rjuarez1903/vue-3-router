<script setup> 
    import { useRouter } from 'vue-router';
    import router from '../router';

    const back = () => {
        router.push('/')
    }
</script>

<template>
    <h1>404</h1>
    <button @click="back" class="btn btn-outline-primary">Volver</button>
</template>