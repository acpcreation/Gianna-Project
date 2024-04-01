<template>
  <div 
    class="scene" 
    v-if="story =! null"
    :style="'background: url(images/locations/'+scene+');'">

    <img 
      class="character" 
      v-for="(iPos, i) in mainStory[index].characters" :key="i"
      :src="'images/characters/'+mainStory[index].characters[i]" 
      alt="Characters"
      :style="characterAlignment[i]">
      

    <Dialogue :text="mainStory[index].dialogue[dialogue]" @click="continueStory()"/>
    <!-- story[index].dialogue[dialogue] -->

  </div>
</template>

<script>
import Dialogue from '@/components/Dialogue.vue'


export default {
  name: 'HomeView',
  components: {
    Dialogue
  },
  data() {
    return {
      index: 0,
      dialogue: 0,
      mainStory: null,
      scene: "beach.jpeg",
      characterAlignment: ["right: 5vw;", "left: 5vw;"]
    }
  },

  created() {
    this.loadStory1()
  },

  mounted() {
    let that = this;
    window.addEventListener("keydown", function (event) {
      switch (event.key) {
        case "ArrowRight":
          that.continueStory();
          break;
        default:
          return;
      }
    });
  },

  methods: {
    loadStory1: function () {
      this.mainStory = null;
      this.mainStory = [
        {
          characters: [],
          dialogue:["CLICK TO START (or press the right arrow key)"]
        },
        {
          characters: ["amongus.png"],
          dialogue:[
            "Jeff: Hi my name jeff",
            "Jeff: My favorite color is blue!"
          ]
        },
        {
          characters: ["amongus.png", "chungus.png"],
          dialogue:[
            "Chungus: Is that my boy Jeff??",
            "Jeff: Wuddup Buggs!",
            "Chungus: It's chill brah. Keepin' it frizzy!",
          ]
        }
      ]
    },

    continueStory: function(){
      if(this.dialogue < this.mainStory[this.index].dialogue.length-1){
        this.dialogue += 1;
      }else{
        this.dialogue = 0;
        if(this.index < this.mainStory.length-1){
          this.index+=1;
        }else{
          this.index = 0;
          alert("Story complete")
        }
        
      }
    }

  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.scene{
  width: 100vw;
  height:100vh;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover !important;
  /* background-size: 300px 100px; */
}

.character{
  height: 40vw;
  position:fixed;
  bottom: 14vh;
}

</style>
