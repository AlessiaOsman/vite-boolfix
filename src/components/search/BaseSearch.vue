<script>
export default {
    name: 'BaseSearch',
    data: () => ({
        searchText: ''
    }),
    emits: ['submit-search', 'text-change'],
    
}
</script>

<template>
    <div>
        <form class="row g-3" @submit.prevent="$emit('submit-search')">
            <div class="col-auto">
            <input class="form-control" @keyup="$emit('text-change', searchText)" type="text" v-model.trim="searchText">
        </div>
        <div class="col-auto">
            <button class="btn btn-danger mb-3">cerca</button></div>

        </form>
    </div>
</template>
