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
    @media only screen and (min-width: 370px) {
        header {
            display: flex;
            margin: 0.5rem 0;
        }

        img {
            margin: 0 0.7rem;
            width: 2rem;
        }

        h1 {
            font-size: 1.2rem;
            display: flex;
            align-items: center;
        }

    }

    @media only screen and (min-width: 992px) {
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
    }
    
</style>
