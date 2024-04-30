<template>
    <div class="btn-group filter_btn">
        <PrimaryButton 
            type="button" 
            :class="[filter === 'all' ? 'btn-dark' : 'btn-outline-dark']"
            @click="filterHandler('all')">Barcha kinolar
        </PrimaryButton>
        <PrimaryButton 
            type="button" 
            :class="[filter === 'most_viewed' ? 'btn-dark' : 'btn-outline-dark']" 
            @click="filterHandler('most_viewed')">Eng ko'p ko'rilgan kinolar
        </PrimaryButton>
        <PrimaryButton 
            type="button" 
            :class="[filter === 'popular' ? 'btn-dark' : 'btn-outline-dark']" 
            @click="filterHandler('popular')">Sevimli kinolar
        </PrimaryButton>
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