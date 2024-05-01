<template>
    <nav aria-label="...">
        <ul class="pagination pagination-sm">
            <li v-for="pageNumber in totalPage" class="page-item" @click="$emit('changePage', pageNumber)" :key="pageNumber" :class="{'active': pageNumber === page}"><span class="page-link">{{ pageNumber }}</span></li>
        </ul>
    </nav>
</template>
<script>
export default {
    props: {
        totalPage: {
            type: Number,
            required: true,
        },
        page: {
            type: Number,
            required: true,
        }
    },
}
</script>
<style>
    
</style>