<template>
  <div class="single-die" :id="dieId">
    {{value}}
  </div>
</template>

<script>
export default {
  props: {
    value: { required: false, type: Number },
    id: { required: true, type: Number }
  },
  data() {
    return {
      dieValue: this.value,
      dieId: `die_${this.id}`
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .single-die {
    box-sizing:border-box;
    width:2em;
    height:2em;
    margin-left:.5em;
    margin-right:.5em;
    vertical-align:middle;
    line-height: 2em;

    border-radius: 5px;
    background-color: white;
    color:#772222;

    font-weight: lighter;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    font-size:1.2em;

  }

  .dice-animate {
    animation-duration:1.5s;
    animation-name:dicepop;
    animation-iteration-count: 1;
  }

  @keyframes dicepop { /* still working on how to hook this animation into the dice-spawning */
    from {
      width:0em;
      height:0em;
    }

    70% {
      width:2.2em;
      height:2.2em;
    }

    to {
      width:2em;
      height:2em;
    }
  }
</style>
