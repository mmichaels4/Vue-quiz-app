<template>
  <div id="app">
    <Header 
    :questionsAnsweredCorrectly="questionsAnsweredCorrectly"
    :questionsAnswered="questionsAnswered"
    />
    

    <b-container v-if="indexOfCurrentQuestion <= 3" class="bv-example-row">
    <!-- <b-container v-if="indexOfCurrentQuestion <= 9" class="bv-example-row"> -->
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox
            v-if="allQuestionDataFromAPI.length"
            :currentQuestionData="allQuestionDataFromAPI[indexOfCurrentQuestion]"
            :nextQuestion="nextQuestion"
            :answeredCorrectly="answeredCorrectly"
            :answeredIncorrectly="answeredIncorrectly"
            :indexOfCurrentQuestion="indexOfCurrentQuestion"
          
            >
          <!-- Data in this tag is sent to the QuestionBox component. It MUST be included in the props section though. -->
          </QuestionBox>
        </b-col>
      </b-row>
    </b-container>
    
    <!-- <DisplayScore v-if="indexOfCurrentQuestion === 10" -->
    <DisplayScore v-if="indexOfCurrentQuestion > 3"
      :questionsAnsweredCorrectly="questionsAnsweredCorrectly"
      :questionsAnswered="questionsAnswered"
      />

    <footer> Test footer </footer>
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
  margin-top: 60px;
}
footer {
  position: fixed;
  bottom: 100;
  width: 100%;
  background-color: blanchedalmond;
}
</style>
