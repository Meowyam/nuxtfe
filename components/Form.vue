<template>
    <body>
        <form>
             <transition-group name="fade">
             <Selector
                v-for="(item, index) in items"
                :key="index"
                :options="options"
                :things="things"
                :mySet="mySet"
                :arr="arr"
                :n="item.n"
            />
            </transition-group>
        </form>
        meow  <button @click="addFormItem()">Add Selector</button>
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
              items: [{ n: 1 }],
              mySet: new Set(),
              things: [],
              arr: [],
            }
        },
        methods: {
            addFormItem() {
                this.items.push({
                  arr: [],
                  options: {},
                  n: this.items.length + 1
                })
                console.log(this.items)
            }
        },
        mounted() {
            this.things = Object.keys(options)
            this.mySet = new Set()
            console.log((Object.values(this.options)[0]).length)

        }
    }
</script>
