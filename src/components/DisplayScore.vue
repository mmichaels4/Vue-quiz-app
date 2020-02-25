<template>
  <div class="container">
    <div class="jumbotron" :class="assignClass()">
      <h1>{{ percentageCorrect }}%</h1>
      <p> You guessed correctly on
        {{ questionsAnsweredCorrectly }} of the 
        {{ questionsAnswered }} questions!
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    questionsAnsweredCorrectly: Number,
    questionsAnswered: Number
  },

  data() {
    return {
       percentageCorrect: 
        (this.questionsAnsweredCorrectly / this.questionsAnswered) * 100
    }
  },

  methods: {
    assignClass() {
      if(this.percentageCorrect <= 25) { return 'lowScore' }
      else if (this.percentageCorrect <= 75) { return 'decentScore' }
      else { return 'goodScore' }
    }
  }
}
</script>

<style scoped>
.lowScore {
  background-color: red;
}

.decentScore {
  background-color: yellow;
}

.goodScore {
  background-color: green;
}
</style>
