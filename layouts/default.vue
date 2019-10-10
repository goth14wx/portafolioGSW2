<template>
<div id="app"  class="back">
  <v-app id="inspire">

    <v-content>
      <v-container>
        <nuxt />

       <window :azureBack="azureB" :iconProp="'public'" :titleProp="'Edge Browser'" class="animated" :class="{'zoomIn':edge,'zoomOut':!edge}" v-if="edge">
         <azure @cb="cba"/>
       </window>
      </v-container>
    </v-content>

     <v-bottom-navigation
    class="d-flex justify-start black"
    :value="activeBtn"
    color="deep-blue accent-4"
    horizontal
      height="45px"
      :fixed="true"
  >
    <v-btn tile >
      <img src="@/assets/img/win.png" height="40px" width="40px"/>
    </v-btn>

    <v-btn id="v-step-0" tile @click.prevent="edge= edge ? false:true">
      <img src="@/assets/img/edge.png" height="40px" width="40px"/>
    </v-btn>

    <v-btn tile >
      <img src="@/assets/img/visual.png" height="40px" width="40px"/>
    </v-btn>
  </v-bottom-navigation>
   <v-tour name="kickstart" :steps="steps"></v-tour>
  </v-app>
</div>
</template>

<script>
import azure from "@/components/azure";
import window from "@/components/window";
export default {
  data(){
    return{
      activeBtn:false,
      edge:false,
      steps: [
          {
            target: '#v-step-0',  // We're using document.querySelector() under the hood
            content: `Empecemos, Abre Edge browser`
          }
      ],
 myOptions: {
          useKeyboardNavigation: false,
          labels: {
            buttonSkip: 'Skip tour',
            buttonPrevious: 'Previous',
            buttonNext: 'Next',
            buttonStop: 'Finish'
          },

 },
  azureB:false,
    }
  },
  components:{
    window,
    azure
  },
  methods:{
    alertThis(){
      alert("hola");
    },
    cba(e){
      this.azureB = e;
    }
  },
    mounted(){
      this.$tours['kickstart'].start()
    }
}
</script>
