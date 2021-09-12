<template>
    <body>
        <form>
            <!-- <LazySelector :options="options" :things="things" :mySet="mySet" :arr="arr" :n="n">
            </LazySelector> -->
            <component v-for="(item, index) in items"
             :key="index"
             :is="item" />
            <!-- <selector :options="options" :things="things" :mySet="mySet" :arr="arr" :n="n">
            </selector> -->
            <!-- <div v-for="(formItem, index) in formItems" :key="index">
                {{formItem}}
            </div> -->
            <!-- <div v-for="(formItem, index) in formItems" :key="index">
            {{formItem}}
            {{index}}
            </div> -->
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

    const Sel = {
        // props: ["options","things","mySet","arr","n"],
        // template: '<selector :options=options :things=things :mySet=mySet :arr=arr :n=n> </selector>'
        template: '<LazySelector :options=this.options></LazySelector>'
    }

    export default {
        data() {
            return {
            options,
            things: null,
            mySet: null,
            arr: [],
            n: 1,
            items: [Sel]
            }
        },
        methods: {
            addFormItem() {
                this.items.push(Sel)
                console.log(this.items)
            }
        },
        computed: {
            selector() {
                return () => import('./Selector')
            }
        },
        mounted() {
            this.things = Object.keys(options)
            this.mySet = new Set()
            console.log((Object.values(this.options)[0]).length)
        }
    }
</script>
