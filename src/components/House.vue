<template>
  <div class="house">
    <h1>Customise your dream house</h1>
    <h2>Add annex to<br/>basic two-storey house</h2>
    <ul>
      <li><Garage @trigger="rebuild"/></li>
      <li><Verand @trigger="rebuild"/></li>
      <li><Balcony @trigger="rebuild"/></li>
      <li><Attic @trigger="rebuild"/></li>
    </ul>
    <iframe :src="'http://127.0.0.1:8081/'+modules+'.html'" onload="spinner=false"></iframe>
    <div v-if="spinner" class="lds-facebook"><div></div><div></div><div></div></div>
  </div>
</template>

<script>
import Garage from "./Garage"
import Verand from "./Verand"
import Balcony from "./Balcony"
import Attic from "./Attic"

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'House',
  components: {
    Garage,
    Verand,
    Balcony,
    Attic
  },
  methods: {
    rebuild: function(e) {
      let key = e[0]
      this.state[key] = e[1]
      let model = ''
      for(let i in this.state){
        model += this.state[i]
      }
      this.modules = 'house'+model
      this.spinner = true
      let a = setTimeout(()=>{this.spinner=false;clearTimeout(a);}, 6000)
    },
  },
  data: ()=>({
    modules: 'house',
    spinner: false,
    state: {
      "garage": "",
      "verand": "",
      "balcony": "",
      "attic": ""
    }
  }),
}
</script>

<style scoped>
.house {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  background-color:red;
  display: flex;
  flex-direction: column;
}
h1{
  position: absolute;
  z-index: 5;
  left: 1em;
  top: 1em;
  font-size: 3rem;
  justify-content: center;
  color: #415675FF;
}
iframe {
  position: absolute;
  height: 100%;
  width: 100%;
  margin: 0;
  padding: 0;
  flex-grow: 1;
  border: none;
  background-color: grey;
}
h2 {
  position: absolute;
  z-index: 5;
  left: 2em;
  top: 4em;
  margin: 40px 0 0;
  text-align: left;
  color: #718fc8;
}
ul {
  position: absolute;
  z-index: 5;
  bottom: 5em;
  list-style-type: none;
  left: 50%;
  transform: translate(-50%, 0);
  background-color: #415675FF;
  height: 3rem;
  width: 28rem;
  border-radius: 1em;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0;
  padding: 0;
  height: 100%;
  width: 25%;
  background: transparent;
}
.lds-facebook {
  display: inline-block;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, 0);
  width: 80px;
  height: 80px;
}
.lds-facebook div {
  display: inline-block;
  position: absolute;
  left: 8px;
  width: 16px;
  background: #fff;
  animation: lds-facebook 1.2s cubic-bezier(0, 0.5, 0.5, 1) infinite;
}
.lds-facebook div:nth-child(1) {
  left: 8px;
  animation-delay: -0.24s;
}
.lds-facebook div:nth-child(2) {
  left: 32px;
  animation-delay: -0.12s;
}
.lds-facebook div:nth-child(3) {
  left: 56px;
  animation-delay: 0s;
}
@keyframes lds-facebook {
  0% {
    top: 8px;
    height: 64px;
  }
  50%, 100% {
    top: 24px;
    height: 32px;
  }
}
</style>
