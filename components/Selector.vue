<template>
    <div>
        <div v-for="(value, name, index) in options" :key="index">
            <v-select
            :options="value"
            @input="name => updatePlayer(name, index, n)">
            </v-select>
            <!-- <v-select
            :options="value"
            @input="name => updatePlayer(name,index,n)">
            </v-select> -->
        </div>
    </div>
</template>
<!--(value, name, index)-->

<script>
export default{
    name: 'selector',
    props: {
        options: Object,
        things : Array,
        mySet  : Set,
        arr    : Array,
        n      : Number,
    },
    methods: {
        updatePlayer(x, i, n) {
            if ((i+1) == Object.keys(this.options).length) {
                this.mySet.add(this.arr)
                this.$emit("addSelect")
            } else {
                let a = this.things[i]
                let b = ("entry" + i)
                b = {}
                b[a] = x
                let c = b[a]
                this.arr.push(c)
            }
        }
    }
}
</script>

