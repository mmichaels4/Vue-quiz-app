<template>
  <div class="box-for-question-cells">
    <b-jumbotron>

      <template v-slot:lead>
        {{ currentQuestionData.question }}
      </template>

      <hr class="my-4">

      <b-list-group
        v-for="(eachAnswer, index) in shuffledAnswers" 
        :key="index"
        @click="selectAnswer(index)"
        >

        <b-list-group-item button>{{ eachAnswer }}</b-list-group-item>
      </b-list-group>


      <b-button @click="checkIfCorrectAnswer(index)" variant="info" href="#">Submit</b-button>
      <b-button @click="nextQuestion" variant="dark" href="#">Next Question</b-button>    
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  // Props is where you 'import' the data from App.vue
  props: {
    currentQuestionData: Object,
    nextQuestion: Function,
  },

  data() {
    return {
      selectedIndex: null,
      indexOfCorrectAnswer: null,
      shuffledAnswers: []
    }
  },

  watch: {
    currentQuestionData: {
      immediate: true,
      handler() {
        this.selectedIndex = null
        this.combineAndShuffleAnswers()
      }
    }
  },

  methods: {
    selectAnswer(index) {
      this.selectedIndex = index
    },

    combineAndShuffleAnswers() {
      let allAnswers = [...this.currentQuestionData.incorrect_answer]
      allAnswers.push(this.currentQuestionData.correct_answer)

      let newIndexOfCorrectAnswer = Math.round(Math.random() * 3)

      let temp = allAnswers[newIndexOfCorrectAnswer]
      allAnswers[newIndexOfCorrectAnswer] = allAnswers[3]
      allAnswers[3] = temp

      this.shuffledAnswers = allAnswers
    }
  }
}
</script>

<style scoped>
.list-group {
  margin-bottom: 10px;
}

.list-group-item:hover {
  cursor: pointer;
}

.btn {
  margin: 0 5px;
}

.selected {
  background-color: darkgrey;
}

.correct {
  background-color: seagreen;
}

.incorrect {
  background-color: tomato;
}
</style>