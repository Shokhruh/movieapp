<template>
    <h1>BARCHA KINOLAR SONII: {{ allMoviesCount }}</h1>
    <h2>SEVIMLI KINOLAR SONI: {{ likedMoviesCount }}</h2>
</template>

<script>
    export default {
        props: {
            allMoviesCount: {
                type: Number,
                required: true,
            },
            likedMoviesCount: {
                type: Number,
                required: true,
            },
        }
    }
</script>

<style>
    
</style>
