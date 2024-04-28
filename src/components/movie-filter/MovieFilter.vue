<template>
    <div class="btn-group filter_btn">
        <button 
            type="button" 
            class="btn btn-dark" 
            @click="filterHandler('all')">Barcha kinolar
        </button>
        <button type="button" class="btn btn-outline-dark" @click="filterHandler('most_viewed')">Eng ko'p ko'rilgan kinolar</button>
        <button type="button" class="btn btn-outline-dark" @click="filterHandler('popular')">Sevimli kinolar</button>
    </div>
</template>

<script>
    export default {
        props: {
            updateFilterHandler: {
                type: Function,
                required: true,
            },
        },
        data() {
            return {
                filter: 'all',
            }
        },
        methods: {
            filterHandler(filter) {
                this.filter = filter,
                this.updateFilterHandler(this.filter)
            }
        },
    }
</script>

<style>
    
</style>