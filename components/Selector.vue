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
        n      : Number
    },
    methods: {
        updatePlayer(x, i, n) {
            console.log(this.things)
            console.log(x)
            console.log(i)
            this.addSelect = false
            let a = this.things[i]
            let b = ("entry" + i)
            b = new Object()
            b[a] = x
            let c = b[a]
            console.log(b)
            console.log(a, b, c)
            console.log(this.arr)
            this.arr.push(c)
            console.log(c)
            console.log(n)
            //this.checkIfEnd(x,c,i,n)
        },
        checkIfEnd(x,c,i,n) {
            console.log(c)
            if ((i+1) == Object.keys(this.options).length) {
                this.mySet.add(this.arr)
                console.log(this.arr)
                console.log(this.mySet)
            } else {
                // this.updatePlayer(x,c,i)
            }
        }
    },
}
</script>

