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
        <form @submit.prevent="$emit('submit-search')">
            <input @keyup="$emit('text-change', searchText)" type="text" v-model.trim="searchText">
            <button>cerca</button>
        </form>
    </div>
</template>