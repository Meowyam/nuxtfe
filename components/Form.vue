<template>
    <body>
        <form>
            <div v-for="(value, name, index) in options">
                <v-select
                :options="value"
                @input="name => updatePlayer(game,name,index)">
                </v-select>
                <!-- <v-select
                :options="option.players"
                @input="(player) => updatePlayer(game, player)">
                </v-select>
                <v-select
                :options="option.moves"
                @input="(move) => updateMove(game, move)">
                </v-select> -->
            </div>

        </form>
        meow
        <div>
            {{game}}
        </div>
    </body>
</template>

<script>
    import vSelect from 'vue-select'
    import Vue from 'vue'
    Vue.component('v-select', vSelect)
    import options from '../static/rules'

    export default {
        data() {
            return {
            options,
            game: {players: '', move: ''}
            }
        },
        methods: {
            updatePlayer(x,y,i) {
                console.log(i)
                let b = (Object.keys(x)[i])
                this.game[b] = y
            },
            updateMove(game, x) {
                game.move = x
            }
        },
    }
</script>
