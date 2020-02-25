<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled>
        Quiz-O-Tron 5000
      </b-nav-item>
      <b-nav-item disabled>
        Score: {{ questionsAnsweredCorrectly }}/{{ questionsAnswered }}
      </b-nav-item>
    </b-nav>
  </div>
</template>


<script>
export default {
  // Props is where you 'import' the data from App.vue
  props: [
    'questionsAnsweredCorrectly',
    'questionsAnswered'
  ]
}
</script>