<template>
    <li class="list-group-item d-flex justify-content-between">
        <span class="list-group-item-label" v-on:click="$emit('onToggle', {id: movie.id, prop: 'liked'})">{{ movie.name }}</span>
        <input type="text" class="list-group-item-input" readonly v-bind:value='movie.seen_count'>
        <div class="d-flex justify-content-center align-items-center">
            <button type="button" class="btn-cookie btn-sm" v-on:click="$emit('onToggle', {id: movie.id, prop: 'favourited'})"><i class="fas fa-cookie"></i></button>
            <button type="button" class="btn-trash btn-sm"><i class="fas fa-trash"></i></button>
            <i class="fas fa-star star"></i>
        </div>
    </li>
</template>

<script>
    export default {
        props: {
            movie: {
                type: Object,
                required: true,
            }
        },
        methods: {
            
        }
    }
</script>

<style scoped>
    .list-group-item {
        padding: 15px 20px;
        border: none;
        /* background-color: #fcfaf5; */
        border-bottom: 1px solid #3d5a80;
    }

    .list-group-item:last-child {
        border-bottom: none;
    }

    .list-group-item span {
        line-height: 35px;
        font-size: 20px;
        cursor: pointer;
        width: 550px;
    }

    .list-group-item input {
        line-height: 35px;
        font-size: 20px;
        text-align: center;
        border: none;
        outline: none;
    }

    .list-group-item button {
        width: 35px;
        height: 35px; 
        margin: 3px;
        font-size: 17px;
        border: none;
        cursor: pointer;
    }

    .list-group-item button.btn-cookie {
        color: #e09f3e;
    }

    .list-group-item button.btn-trash {
        color: #e5383b;
    }

    .star {
        width: 35px;
        height: 35px;
        text-align: center;
        line-height: 35px;
        font-size: 16px;
        color: #ffd700;
        transform: 0.3s all;
        transform: translate(30px);
        opacity: 0;
    }

    .list-group-item.liked .star {
        opacity: 1;
        transform: translate(0);
    }

    .list-group-item.favourited span, .list-group-item.favourited input {
        color: #e09f3e;
    }
</style>