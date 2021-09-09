<template>
    <body>
        <form>
            <div v-for="(value, name, index) in options">
                <v-select
                :options="value"
                @input="name => updatePlayer(name,index)">
                </v-select>
            </div>

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
            arr: [],
            things: null,
            mySet: null
            }
        },
        methods: {
            updatePlayer(x,i) {
                console.log(x,i)
                let a = this.things[i]
                let b = ("entry" + i)
                b = new Object()
                b[a] = x
                let c = b[a]
                console.log(b)
                console.log(a, b, c)
                //let c = a[b]
                this.arr.push(c)
                //console.log(a[b])
                this.checkIfEnd(x,i)
            },
            checkIfEnd(x,i) {
                console.log((i+1) == (Object.keys(this.options).length))
                // if ((i) == Object.keys(this.options).length) {
                //     mySet.add(c)
                //     this.arr = []
                //     console.log(mySet)
                // } else {
                //     this.updatePlayer(x,i)
                // }
            }
        },
        mounted() {
            this.things = Object.keys(options)
            this.mySet = new Set()
            console.log(this.things)
        }
    }
</script>
