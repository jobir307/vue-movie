<template>
    <div class="list-group-item d-flex justify-content-between" v-bind:class="[{like: movie.like}, {favourite: movie.favourite}]">
        <span class="list-group-item-label" v-on:click="$emit('onToggle', {id: movie.id, prop: 'like'})">{{ movie.name }}</span>
        <input type="number" class="list-group-item-input" v-bind:value="movie.viewers">
        <div class="d-flex justify-content-center align-items-center">
            <button type="button" class="btn btn-cookie btn-sm" v-on:click="$emit('onToggle', {id: movie.id, prop: 'favourite'})">
                <i class="fas fa-cookie"></i>
            </button>
            <button type="button" class="btn btn-trash btn-sm" v-on:click="$emit('onDelete', movie.id )">
                <i class="fas fa-trash"></i>
            </button>
            <i class="fas fa-star"></i>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'movie-list-item',
        props: {
            movie: {
                type: Object,
                required: true
            }
        }
    }
</script>

<style scoped>
.list-group-item {
    padding: 15px 20px;
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
    border: 0;
    outline: none;
}

.list-group-item button {
    width: 35px;
    height: 35px;
    font-size: 16px;
}

.list-group-item .btn-cookie {
    color: #c5821d;
}

.list-group-item .btn-trash {
    color: #cf240e;
}

.list-group-item .fa-star {
    width: 35px;
    height: 35px;
    text-align: center;
    color: hsl(60, 83%, 47%);
    line-height: 35px;
    font-size: 16px;
    transition: 0.3s all;
    transform: translateX(30px);
    opacity: 0;
}
.list-group-item.like .fa-star {
    opacity: 1;
    transform: translateX(0);
}
.list-group-item.favourite .list-group-item-label, 
.list-group-item.favourite .list-group-item-input {
    color: #d68814;
}
</style>