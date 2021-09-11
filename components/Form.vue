<template>
    <body>
        <form>
            <selector :options="options" :things="things" :mySet="mySet" :arr="arr" :n="n">
            </selector>
        </form>
        meow
        <div>
            {{arr}}
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
            things: null,
            mySet: null,
            arr: [],
            n: 1,
            }
        },
        mounted() {
            this.things = Object.keys(options)
            this.mySet = new Set()
            console.log((Object.values(this.options)[0]).length)
        }
    }
</script>
