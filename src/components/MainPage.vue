<template>
    <main>
        <div>
            <input @keyup.enter="getResponse()" v-model="query" type="text">
            <button @click="getResponse()" :disabled="query.length === 0">invia</button>
        </div>

        <div>
            <ul v-for="pokemon,i in pokemons">
                <li>{{pokemon.name}}</li>
                <li>{{pokemon.height}}</li>
                <li>{{pokemon.weight}}</li>
            </ul>

            <ul v-for="tipo in types">
                <li>{{tipo.name}}</li>
                <li>{{tipo.name}}</li>
            </ul>

            <ul v-for="item in stats">
                <li>{{item.hp}}</li>
                <li>{{item.attack}}</li>
                <li>{{item.defence}}</li>
                <li>{{item.sp_attack}}</li>
                <li>{{item.sp_defence}}</li>
                <li>{{item.speed }}</li>
            </ul>
        </div>
    </main>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            pokemons: [],
            stats:[],
            types:[],
            query: '',
        }
    },
    methods: {
        pokemonResponse() {
            axios.get(`https://pokeapi.co/api/v2/pokemon/${this.query}`)
            .then((res) => {
                this.pokemons = []
                const data = res.data
                const status = data.stats
                const types = data.types

                for(let j = 0; j < types.lenght; j++){
                    const firstType = types.name
                    // const secondType = types[1].name

                    this.types.push({
                        firstType,
                        // secondType
                    })

                };

                for(let i = 0; i < 1;i++){
                    const hp = status[0].base_stat
                    const attack = status[1].base_stat
                    const defence = status[2].base_stat
                    const sp_attack = status[3].base_stat
                    const sp_defence = status[4].base_stat
                    const speed = status[5].base_stat

                    this.stats.push({
                        hp,
                        attack,
                        defence,
                        sp_attack,
                        sp_defence,
                        speed
                    })
                }
                this.pokemons.push(data)
                // this.pokemons.push(data)
                console.log(res)
                
            })
        },
        getResponse() {
            this.pokemonResponse()
        }
    },
    mounted() {
        // console.log(data)
        // console.log(this.query)
        // console.log(this.status)
        console.log('pokemons: ',this.pokemons)
        console.log('tipo:', this.types)
    }
}
</script>

<style lang="scss" scoped>
*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

ul, ol, menu{
    list-style: none;
}

main {
    padding: 30px;
}
</style>