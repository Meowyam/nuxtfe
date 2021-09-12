<template>
    <div>
        <div v-for="(value, name, index) in options">
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
            console.log('start',x,i,n)
            let a = this.things[i]
            let b = ("entry" + i)
            b = {}
            b[a] = x
            let c = b[a]
            this.arr.push(c)
            this.checkIfEnd(x,c,i,n)
        },
        checkIfEnd(x,c,i,n) {
            console.log(i+1, Object.keys(this.options).length)

            if ((i+1) == Object.keys(this.options).length) {
                this.mySet.add(this.arr)
                console.log('end check',x,c,i,n)
                console.log('in component')
            } else {
                console.log('end',x,c,i,n)
                // this.updatePlayer(x,c,i)
            }
        }
    }
}
</script>

