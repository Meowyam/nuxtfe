<template>
  <div>
      Do you:
    <div v-for="(value, name, index) in options">
      <v-select :options="value" @input="name => updatePlayer(name, index, n)">
      </v-select>
    </div>
  </div>
</template>

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
                console.log(x,i,n)
                b = {}
                b[a] = x
                let c = b[a]
                this.arr.push(c)
            }
        }
    }
}
</script>
