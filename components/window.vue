<template>
 <vue-draggable-resizable :class-name="{'white':true,'color-gradient-azure':azureBackground}"  :w="1200" :x="50" :y="5" :max-width="1300" :min-width="300" :h="560">
    <v-system-bar window dark class="ma-0">
      <v-icon>{{this.icon}}</v-icon>
      <span class="truncate-text">{{this.title}}</span>
      <div class="flex-grow-1"></div>
      <v-icon>mdi-minus</v-icon>
      <v-icon>mdi-checkbox-blank-outline</v-icon>
      <v-icon >mdi-close</v-icon>
    </v-system-bar>

  <slot></slot>
    <!--<v-tour name="myTour" :steps="steps"></v-tour>-->
  </vue-draggable-resizable>
</template>

<script>
  export default {
    props:["titleProp","iconProp","azureBack"],
    data(){
      return{
        title:this.titleProp,
        icon:this.iconProp,
        azureBackground:this.azureBack ? false: true
      }
    },
    watch:{
      azureBack:function(){
        this.azureBackground= true;
      }
    }
  }
  </script>
