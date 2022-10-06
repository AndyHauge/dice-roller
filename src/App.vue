<template>
  <div id="main_app">
    <h1>Roll Those Bones</h1>
    <ul>
      <li v-for="die in DiceList" :key="die.id">
        <single-die :id="die.id" :value="die.value"></single-die>
      </li>
    </ul>
    <h2 id="dice-sum">Dice Total: {{diceSum}}</h2>
    <roll-submit @die-rolled="rollDie" @dice-reset="diceClear"></roll-submit>
  </div>
  
</template>

<script>
import SingleDie from './components/SingleDie.vue';
import RollSubmit from './components/RollSubmit.vue';

export default {
  name: 'App',
  components: {
    SingleDie,
    RollSubmit
  },
  methods: {
    rollDie(){ 
      this.diceClear();
      for (let i = 1; i <= 5; i++) {
        this.DiceList.push({id:i,value:Math.floor(Math.random()*6) + 1}); // pushes a d6 roll into the array
      }
     }, // Called when "die-rolled" emitted
    diceClear(){
      this.DiceList.length = 0; // collapses array, removing all dice as a consequence
    },
  },
  computed: {
    diceSum() {
      let diceTotal = 0;
      for (const die of this.DiceList){
        diceTotal += die.value;
      }
      return diceTotal;
    },
  },
  data() {
    return {
      DiceList: [] // container for dice
    };
  }
};
</script>

<style>
/* General styles */


.btn {
  border:0.3em solid #FFFFFF;
  border-radius:0.5em;
  background-color: #FFAAAA;
  color:#333355;
}

.btn:hover {
  background-color:#BB2200;
  color:#FFFFFF;
}

#main_app {
  text-align:center;
  padding:4em;
  width:40em;
  margin-top:2em;
  background-color: #772222;
  color:#FFFFDD;
  border-radius:0.7em;
}

#app ul {
  display:flex;
  justify-content: center;
  min-height: 3em; /* syncs with die size as set in SingleDie.vue */
}


</style>
