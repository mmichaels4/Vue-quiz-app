<template>
  <div class="box-for-question-cells">
    <b-jumbotron>

      <template v-slot:lead>
        {{ currentQuestionData.question }}
      </template>

      <hr class="my-4">

      <b-list-group
        v-for="(eachAnswer, index) in allAnswers" 
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
      allAnswers: []
    }
  },

  watch: {
    currentQuestionData: {
      immediate: true,
      handler: function() {
        this.selectedIndex = null
        this.combineIncorrectAndCorrectAnswers()
        this.shuffleAnswers()
      }
    }
  },

  methods: {
    selectAnswer(index) {
      this.selectedIndex = index
    },

    combineIncorrectAndCorrectAnswers() {
      this.allAnswers = [...this.currentQuestionData.incorrect_answers]
      this.allAnswers.push(this.currentQuestionData.correct_answer)
      this.indexOfCorrectAnswer = (this.allAnswers.length - 1)
    },

    shuffleAnswers() {
      let oldIndexOfCorrectAnswer = this.indexOfCorrectAnswer
      this.indexOfCorrectAnswer = Math.round(Math.random() * 3)

      var temp = this.allAnswers[this.indexOfCorrectAnswer]
      this.allAnswers[this.indexOfCorrectAnswer] = this.allAnswers[oldIndexOfCorrectAnswer]
      this.allAnswers[oldIndexOfCorrectAnswer] = temp
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