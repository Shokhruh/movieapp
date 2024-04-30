<template>
    <div class="movie_add_form">
        <h3>Yangi kino qo'shish</h3>
        <form action="" class="add_movie d-flex" @submit.prevent>
            <Input type="text" class="add_new_movie" placeholder="Kino nomi..." v-model="name" />
            <Input type="number" class="seen_count" placeholder="Ko'rishlar soni..." v-model="seen_count" />
            <PrimaryButton class="btn-dark" type="submit" v-on:click="addMovie">Qo'shish</PrimaryButton>
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