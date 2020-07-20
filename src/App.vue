<template>
<div class="container">
  <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
    <br><br>
    <div class="alert alert-info"><h1 class="text text-center" >Learning Math with Areeg!</h1></div>
    
</div>

<div class="row">
  <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
    <transition name="flip" mode="out-in">
      <component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-question'"></component>

    </transition>
    
  </div>
</div>
</div>
</template>
<script>

import Questions from "./components/Questions";
import Answer from "./components/Answer"
export default {
  data(){
    return{
      mode: 'app-question'
    }
  },
  methods:{
    answered(isCorrect){
      if(isCorrect){
        this.mode = 'app-answer'
      }else{
        this.mode = 'app-question'
        alert('Wrong, try again')
      }
    }

  },
  components:{
    appQuestion: Questions,
    appAnswer: Answer
  }
}
</script>

<style scoped>
.flip{
  /* transform: rotateY(0deg); */
}
.flip-enter-active{
  animation: flip-in 0.5s ease-out forwards

}

.flip-leave{
  transform:  rotateY(0deg);
}

.flip-eave-active{
  animation: flip-out 0.5s ease-out forwards
}

@keyframes flip-out{
  from{
    transform :rotateY(0deg);
  }to{
    transfor : rotateY(90deg);
  }
}

@keyframes flip-in{
  from{
    transform: rotateY(90deg);
  }to{
    transform: rotateY(0deg)
  }
}
</style>