<script>
export default {
    name: 'BaseSearch',
    data: () => ({
        searchText: ''
    }),
    emits: ['submit-search']
}
</script>

<template>
    <div>
        <form @submit.prevent="$emit('submit-search')">
            <input type="text" v-model="searchText">
        </form>
    </div>
</template>