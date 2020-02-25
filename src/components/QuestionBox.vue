<template>
  <div class="box-for-question-cells">
    <b-jumbotron>

      <template v-slot:lead>
        {{ currentQuestionData.question }}
      </template>

      <hr class="my-4">

      <b-list-group>
        <b-list-group-item 
        v-for="(eachAnswer, index) in allAnswers" 
        :key="eachAnswer.index"
        @click.prevent="selectAnswer(index)"
        :class="assignClass(index)"
        >
          {{ eachAnswer }}
        </b-list-group-item>
      </b-list-group>

      <b-button 
      :disabled="selectedIndex === null || answeredTheQuestion === true"
       @click="checkIfCorrectAnswer" variant="info" href="#">Submit</b-button
       >
      <b-button :disabled="answeredTheQuestion === false" @click="nextQuestion" 
      variant="dark" href="#">{{ getButtonText }}</b-button
      >    

    </b-jumbotron>
  </div>
</template>

<script>
export default {
  // Props is where you 'import' the data from App.vue
  props: {
    currentQuestionData: Object,
    nextQuestion: Function,
    answeredCorrectly: Function,
    answeredIncorrectly: Function,
    indexOfCurrentQuestion: Number,
  },

  data() {
    return {
      selectedIndex: null,
      indexOfCorrectAnswer: null,
      allAnswers: [],
      answeredTheQuestion: false,
    }
  },

  computed: {
    getButtonText: function() {
      if (this.indexOfCurrentQuestion === 9)
      {
        return 'See Score'
      }
      else {
        return 'Next Question'
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
    },

    checkIfCorrectAnswer() {
      this.answeredTheQuestion = true

      if (this.selectedIndex === this.indexOfCorrectAnswer) {
        this.answeredCorrectly()
      } else {
        this.answeredIncorrectly()
      }
    },

    assignClass(index) {
      let classToReturn = ''
      if (index === this.selectedIndex && this.answeredTheQuestion === false) {
        classToReturn = 'selected'
      } else if (index === this.indexOfCorrectAnswer && this.answeredTheQuestion === true ) {
        classToReturn = 'correct'
      } else if (index === this.selectedIndex && this.selectedIndex !== this.indexOfCorrectAnswer) {
        classToReturn = 'incorrect'
      }
      return classToReturn
    }
  },

  watch: {
    currentQuestionData: {
      immediate: true,
      handler: function() {
        this.answeredTheQuestion = false
        this.selectedIndex = null
        this.combineIncorrectAndCorrectAnswers()
        this.shuffleAnswers()
      }
    }
  }
}
</script>

<style scoped>
.list-group-item {
  margin-bottom: 10px;
}

.list-group-item:hover {
  cursor: pointer;
  background-color: darkgrey;
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