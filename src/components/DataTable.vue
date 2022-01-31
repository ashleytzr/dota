<template>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Bitter:wght@500&display=swap" rel="stylesheet">
    <header>
        <h1>Top 10 Pro Win Rate Dota Heroes</h1>
    </header>

    <table class="dota-table">
        <tr>
            <th>Hero Image</th>
            <th>Hero Name</th>
            <th>Pro Win Rate</th>
            <th>Pro Pick Count</th>
            <th>Pro Ban Count</th>
        </tr>
        <tr v-for="hero in table" :key="hero.id" class="hero-data">
            <td><img :src="hero.img"/></td>
            <td>{{hero.name}}</td>
            <td>{{hero.pro_win}}</td>
            <td>{{hero.pro_pick}}</td>
            <td>{{hero.pro_ban}}</td>
        </tr>
    </table>
</template>

<script>
import axios from 'axios';
export default {
    name: 'DataTable',
    data() {
        return {
            table: []
        }
    },
    methods: {
        // filterByName: (dotaHeroesArr) => {

        // }
    },
    created() {
        let config = {
            headers: {
                'Accept': 'application/json'
            }
        }

        axios.get('https://api.opendota.com/api/heroStats', config)
        .then(res => {
            this.table = res.data;

            // To sort heroes by top 10 where top is the first hero in the result
            this.table.sort((hero1, hero2) => {
                return hero2.pro_win - hero1.pro_win
            });

            // Get only top 10 pro win rate heroes
            this.table = this.table.slice(0, 10);

            this.table.map(hero => {
                let {name, img} = hero
                name = name.replace('npc_dota_hero_', '');
                name = name.charAt(0).toUpperCase() + name.slice(1);
                hero.name = name.replace('_', ' ');

                hero.img = `https://api.opendota.com${img}`;
            });
        });
    }
}
</script>

<style scoped>
header h1 {
    letter-spacing: 0.09rem;
    font-size: 2.5rem;
    margin: 1.9rem;
    text-align: center;
}

table {
    margin: 1rem auto;
}

table th {
    padding: 1rem 1rem;
    font-size: 1.5rem;
}

table td, table th {
    text-align: center;
    padding: 1.3rem 1rem;
}

tr:nth-child(even) {
    background-color: #6b7b85;
}

tr:nth-child(odd):not(tr:first-child) {
    background-color: #1f262c;
}

table tr:first-child td:first-child {
    border-top-left-radius: 10px;
}

table tr:first-child td:last-child {
    border-top-right-radius: 10px;
}

table tr:last-child td:first-child {
    border-bottom-left-radius: 10px;
}

table tr:last-child td:last-child {
    border-bottom-right-radius: 50px;
}

.hero-data img {
    width: 200px;
    border-radius: 10px;
}
</style>
