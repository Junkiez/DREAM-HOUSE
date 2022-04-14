<template>
  <button @click="process()" :class="state ? 'active' : ''">Verand</button>
</template>

<script>
export default {
  name: "b-Verand",
  data: ()=>({
    state: false,
  }),
  methods: {
    process: function() {
      this.state = !this.state;
      this.$emit("trigger", ["verand", this.state ? "verand" : ""])
    }
  }
}
</script>

<style scoped>
button{
  font-family: BebasNeue, monospace;
  font-size: 2em;
  font-weight: 900;
  width: 100%;
  height: 100%;
  background: transparent;
  border-radius: 1em;
  margin: 0;
  padding: 0;
  border: none;
  color: #00ffa6;
  transition: all 0.35s ease;
}
.active{
  color: violet;
  transition: all 0.35s ease;
}
</style>
