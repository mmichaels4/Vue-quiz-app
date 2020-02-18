<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled>Name of my app</b-nav-item>
      <b-nav-item disabled>Score: {{ numberOfQuestionsGuessedCorrectly }}/{{ numberOfQuestionsSeen }}</b-nav-item>
    </b-nav>
  </div>
</template>


<script>
export default {
  // Props is where you 'import' the data from App.vue
  props: [
    'numberOfQuestionsGuessedCorrectly',
    'numberOfQuestionsSeen'
  ]
}
</script>