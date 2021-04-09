
<!-- I have notes from the video on this-->
<!-- The answer to the question is at the end of this-->


<!-- this is the parent -->
<template>
<div id='app'>

<h1>Would you rather??</h1>
<!--connects wouldyourather.vue template-->
<!-- question is name of prop in wouldyourather-->

<!-- a v-for loop to go through the questions list and v-bind answers from child to answers in list and if answer-changed is recieved it
calls the answerChanged function-->

<wouldyourather
v-for="question in questions"
v-bind:key="question.id"
v-bind:question="question.wyrQuestion"
v-bind:answer1="question.wyrAnswer1"
v-bind:answer2="question.wyrAnswer2"
v-on:answer-changed="answerChanged">
</wouldyourather>
<!-- got help from tutor with the idea for this but changed what he was doing-->
<!-- a list to diplay answers-->
<ul >  
  <li >{{userSelectionMessage[0]}} </li>
  <li >{{userSelectionMessage[1]}} </li>
  <li >{{userSelectionMessage[2]}} </li>
</ul>

</div>
  
</template>

<script>
import wouldyourather from './components/wouldyourather.vue'

export default {
  name: 'App',
  components: {
    wouldyourather
  }, 
  data(){
    return{
      // a list of objects to contain questions and answers to be displayed
      questions: [ 
        {
      // returns to wouldyourather.vue
      id: 0,
      wyrQuestion: 'Would you rather live in a house shaped like a triangle or a circle?',
      wyrAnswer1: 'Triangle',
      wyrAnswer2: "Circle"
        },
        {
      id: 1,    
      wyrQuestion: 'Would you rather have a full suit of armor or a horse?',
      wyrAnswer1: 'armor',
      wyrAnswer2: 'horse'
        },
        {
      id: 2,    
      wyrQuestion: 'Would you rather be incredibly funny or incredibly smart?',
      wyrAnswer1: 'funny',
      wyrAnswer2: 'smart'
    
        }
      ],
      // got help from tutor to make the empty string a list
      userSelectionMessage: []
      }
  },
  methods:{
    //choice if from wouldyourather
    answerChanged(choice){
     // this.userSelectionMessage = `Thanks! you chose ${choice}`
     // got help from tutor to figure out this part, it checks all the answer against all the choices and print choice
      if (this.questions[0].wyrAnswer1 == choice){
        this.userSelectionMessage[0] = choice
        }
        if(this.questions[0].wyrAnswer2 == choice){
          this.userSelectionMessage[0] = choice
        }
         if(this.questions[1].wyrAnswer1 == choice){
          this.userSelectionMessage[1] = choice
        }
         if(this.questions[1].wyrAnswer2 == choice){
          this.userSelectionMessage[1] = choice
        }
         if(this.questions[2].wyrAnswer1 == choice){
          this.userSelectionMessage[2] = choice
        }
         if(this.questions[2].wyrAnswer2 == choice){
          this.userSelectionMessage[2] = choice
        }
    }

  }
}
</script>

<style>
body{
  background: lightskyblue;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-blend-mode: difference;
  
}
</style>
<!-- would you rather question: the component should send the event to process, the answer- the choice, and any updates. The parent knows
what question is asked from what is sent to the question string in child which is sent back, it knows what answer from the v-bind in child.