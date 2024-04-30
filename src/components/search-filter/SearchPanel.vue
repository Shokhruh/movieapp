<template>
    <form>
        <Input type="text" class="search_input" placeholder="Kinolarni qidirish..." v-model="term" @input="changeTermHandler" />
    </form>
</template>

<script>
    export default {
        props: {
            updateTermHandler: {
                type: Function,
                required: true,
            }
        },
        data() {
            return {
                term: '',
            }
        },
        methods: {
            changeTermHandler(e) {
                this.term = e.target.value
                this.updateTermHandler(this.term)
            }
        }
    }
</script>

<style scoped>
    form {
        margin-bottom: 1rem;
    }

    .search_input {
        padding: 1.5rem;
        border-radius: 4px;
        background-color: #fcfaf5;
    }
</style>