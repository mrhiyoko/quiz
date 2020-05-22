<template>
  <div id="app">
    <b-container>
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox/>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
  import QuestionBox from "@/components/QuestionBox";
  import axios from 'axios';

  export default {
    name: 'app',
    components: {
      QuestionBox
    },
    data() {
      return {
        questions: []
      }
    },
    mounted: function () {
      axios.get('https://opentdb.com/api.php?amount=10&category=27&type=multiple')
      .then((response) => {
        console.log(response.data)
      })
      .then((data) => {
        this.questions = data.results;
      })
      .catch(error => {
        console.log(error)
      });
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
</style>
