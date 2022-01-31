<template>
    <header>
        <img src="../assets/dota-2.png" />
        <h1> Dota 2</h1>
    </header>
</template>

<script>
    export default {
        name: 'Header'
    }
</script>

<style scoped>
    header {
        display: flex;
    }

    img {
        margin: 0 1.2rem;
        width: 4.5rem;
    }

    h1 {
        font-size: 1.8rem;
        display: flex;
        align-items: center;
    }
</style>
