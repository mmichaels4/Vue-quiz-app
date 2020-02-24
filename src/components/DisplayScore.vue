<template>
  <div>
    <p :class="assignClass"> Your score was {{ questionsAnsweredCorrectly }}/{{ questionsAnswered }} - {{ getPercentage }}%</p>
  </div>
</template>

<script>
export default {
  // props: [
  //   'questionsAnsweredCorrectly',
  //   'questionsAnswered'
  // ],

  props: {
    questionsAnsweredCorrectly: Number,
    questionsAnswered: Number
  },

  // data() {
  //   percentageCorrect: Number
  // },

  computed: {
    getPercentage: function() {
      return (this.questionsAnsweredCorrectly / this.questionsAnswered) * 100
    }
  }, 

  methods: {
    assignClass() {
      if(this.getPercentage <= 25) {
        return 'lowScore'
      }
      if (this.getPercentage <= 75) {
        return 'decentScore'
      }
      else {
        return 'goodScore'
      }
    }
  }


}
</script>

<style scoped>
lowScore {
  font-size: xx-large;
  color: red;
}

decentScore {
  font-size: xx-large;
  color: yellow;
}

goodScore {
  font-size: xx-large;
  color: green;
}

</style>