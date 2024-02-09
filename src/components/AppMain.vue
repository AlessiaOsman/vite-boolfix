<script>
    export default{
        name: 'AppMain',
    }
</script>
<template>
    <main class="flex-grow-1">
    <slot></slot>
    </main>
</template>

<style lang="scss" scoped>
    main{
        padding: 32px;
        background-color: black;
        height: 100%;
        overflow: auto;
    }
</style>