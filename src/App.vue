<template>
  <div id="app">
    
    <Header class="headerClass"
    :questionsAnsweredCorrectly="questionsAnsweredCorrectly"
    :questionsAnswered="questionsAnswered"
    />

    <b-container v-if="indexOfCurrentQuestion <= 9" class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox
            class="questionBoxClass"
            v-if="allQuestionDataFromAPI.length"
            :currentQuestionData="allQuestionDataFromAPI[indexOfCurrentQuestion]"
            :nextQuestion="nextQuestion"
            :answeredCorrectly="answeredCorrectly"
            :answeredIncorrectly="answeredIncorrectly"
            :indexOfCurrentQuestion="indexOfCurrentQuestion"
            />
        </b-col>
      </b-row>
    </b-container>
    
    <DisplayScore class="displayScore"
      v-if="indexOfCurrentQuestion === 10"
      :questionsAnsweredCorrectly="questionsAnsweredCorrectly"
      :questionsAnswered="questionsAnswered"
      />

    <footer class="fixed-bottom"> Created by Matty Michaels following a YouTube
      <a href="https://www.youtube.com/watch?v=4deVCNJq3qc&t=2133s" 
        target="_blank">Tutorial</a>, but added more functionality and 
      (theoretically) reduced the complexity of the code. Her code can be seen 
      <a href="https://github.com/gwenf/vue-quiz" target="_blank">here</a>.
    </footer>

  </div>
</template>

<script>
import Header from './components/Header.vue'
import QuestionBox from './components/QuestionBox.vue'
import DisplayScore from './components/DisplayScore.vue'

export default {
  name: 'App',

  components: {
    Header,
    QuestionBox,
    DisplayScore
  },

  data() {
    return {
      allQuestionDataFromAPI: [],
      questionsAnsweredCorrectly: 0,
      questionsAnswered: 0,
      indexOfCurrentQuestion: 0,

    }
  },

  methods: {
    nextQuestion(){
      this.indexOfCurrentQuestion++
    },

    answeredCorrectly() {
      this.questionsAnsweredCorrectly++
      this.questionsAnswered++
    },

    answeredIncorrectly() {
      this.questionsAnswered++
    }
  },

  mounted: function() {
    fetch ('https://opentdb.com/api.php?amount=10&category=9&difficulty=easy&type=multiple', {
      method: 'get'
    })
      .then((response) => {
        return response.json()
      })
      .then((jsonData) => {
        this.allQuestionDataFromAPI = jsonData.results
      })
  } 

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}

footer {
  bottom: 100;
  width: 100%;
  background-color: #edeff0;
}

.headerClass {
  background-color: #edeff0;
}

.questionBoxClass {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.displayScore {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
