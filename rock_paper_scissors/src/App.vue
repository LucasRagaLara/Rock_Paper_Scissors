<template>
  <div id="App">
    <header class="menu">
      <HeaderUp :cont="cont"></HeaderUp>
    </header>
      <ContainGame @update_number="update_count"></ContainGame>
      <PopUpRules/>
  </div>
</template>

<script>
import PopUpRules from './components/PopUpRules.vue';
import HeaderUp from './components/HeaderUp.vue';
import ContainGame from './components/ContainGame.vue';
export default {
  name: 'App',
  data() {
    return {
    cont: 0
    };
  },
  methods: {
    update_count(cont) {
        console.log('Evento update_number recibido con valor:', cont);
        this.cont = cont;
    }
  },
  components: {
    PopUpRules,
    HeaderUp,
    ContainGame
  }
}
</script>
<style lang="sass">
  *
    margin: 0
    padding: 0
    box-sizing: border-box
    font-family: 'Barlow Semi Condensed', sans-serif
  #App
    width: 100%
    background: radial-gradient(hsl(214, 47%, 23%), hsl(237, 49%, 15%))
    background-size: cover
    min-height: 100vh
</style>
