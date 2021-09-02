<template>
    <body>
        <div v-for="option in options" :key="option.id">
            <form>
                <v-select
                :options="option.players"
                @input="(player) => updateGame(game, player)">
                </v-select>
                <v-select
                :options="option.moves"
                @input="(move) => updateGame(game, move)">
                </v-select>
            </form>
        </div>
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
              game: {player: '', move: ''}
            }
        },
        methods: {
            updateGame(game, player) {
                game.player = player
            }
        },
    }
</script>
