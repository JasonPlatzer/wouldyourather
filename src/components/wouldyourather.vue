<template>
  <div class="wyr">

    <h2>Please make your choice</h2>
  <!-- from App-->
    <h3> {{ question}} </h3>
    
    
    <!-- v-model="choice"  and v-bind value in both makes it so only one can be selected v-bind sets value-->
    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade"><label>{{ answer1 }}</label>
    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade"><label>{{ answer2 }}</label>
    
    
    
  </div>
  


</template>

<script>
export default {
  name: 'wouldyourather',
  // stores data from App.vue
  // a prop is provided by a parent
  props: {
    question: String,
    answer1: String,
    answer2: String
  },
  data(){
    return{
      choice: ''

    }
  },
  methods:{
    choiceMade(){
      // answer-changed is an event
  // this.$emit sends to App
      this.$emit('answer-changed', this.choice)
    }


  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.wyr{
  border: 2px black solid;
  background-color: lightseagreen;
  outline-style: dashed;
}

</style>
