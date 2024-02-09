<script>
    export default{
        name: 'AppMain',
    }
</script>
<template>
    <main>
    <slot></slot>
    </main>
</template>

<style lang="scss" scoped>
    main{
        padding: 32px;
        background-color: black;
    }
</style>