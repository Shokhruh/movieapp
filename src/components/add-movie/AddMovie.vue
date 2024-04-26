<template>
    <div class="movie_add_form">
        <h3>Yangi kino qo'shish</h3>
        <form action="" class="add_movie d-flex" @submit.prevent>
            <input type="text" class="form-control add_new_movie" placeholder="Kino nomi..." v-bind:value='name' @input="name = $event.target.value">
            <input type="number" class="form-control seen_count" placeholder="Ko'rishlar soni..." v-bind:value='seen_count' v-on:input="seen_count = $event.target.value">
            <button class="btn btn-dark" v-on:click="addMovie">Qo'shish</button>
        </form>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: '',
                seen_count: '',
            }
        },
        methods: {
            addMovie() {
                const newMovie = {
                    name: this.name,
                    seen_count: this.seen_count,
                    liked: false,
                    favourited: false,
                };
                this.$emit('createMovie', newMovie);
                this.name = '';
                this.seen_count = '';
            }
        }
    }
</script>

<style>

</style>