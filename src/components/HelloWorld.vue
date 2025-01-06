<template>

</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
  return {
   items:Array.from({length:1000},(_,i) => `Item,${i}`)
  };
},
mounted() {
 console.log(this.items,"111")
},
methods: {

},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
</style>
