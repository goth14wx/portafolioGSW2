<template>
<div>
             <v-app-bar
      color="#1a1a1f"
      dark
      height="50px"
      flat
    >

      <v-toolbar-title> <logomicrosoft/></v-toolbar-title>

      <div class="flex-grow-1"></div>
      <v-btn icon>
        <v-icon>phone</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container fluid class="mt-0 pt-0 " v-if="login">
  <v-row class="black--text mt-0" style="background-color:#ececec" >
    <v-col class="mt-0 d-flex justify-start" cols="4" sm="4">
      <strong class="font-ubuntu text-truncate">Azure Dev Tools for Teaching</strong>
    </v-col>
    <v-col cols="6" sm="6" class="pa-0" :align-self="'center'">
      <v-skeleton-loader
      v-for="i in 5"
      :key="i"
      type="avatar"
      class="white ml-10 d-inline-block"
      max-width="50px"
      max-height="40px"
    ></v-skeleton-loader>
    </v-col>
    <v-col class="d-flex flex-row-reverse" i col="2" sm="2" :align-self="'center'">
      <v-btn tile depressed="" id="v-step-0" style="color:#7b7b7b" icon @click="changeBackground">

        <v-icon >person_outline</v-icon>
      </v-btn>
      <v-btn tile depressed="" icon class="black--text">
        <v-icon>shopping_cart</v-icon>
      </v-btn>

<v-tour name="login" :steps="steps"></v-tour>
    </v-col>
  </v-row>
  <v-row>
    <v-col cols="12" sm="12" class="black--text font-abel">
      <p>
        Students—you’re almost there! The developer tools and learning resources that were previously part of your Imagine account are now available with Azure Dev Tools for Teaching. Sign in using the button below—you’ll be taken to a page requesting you to sign in using a Microsoft Account. Learn about Microsoft Accounts here.Note: Please use the email you provided for your previous Imagine subscription access when creating a new Microsoft Account.
      </p>
      <div>
        if you are having issues getting access, please reference our <span class="blue--text">help guide</span>. For additional support, please check out <span class="blue--text">student FAQ.</span>
      </div>
    </v-col>
  </v-row>
</v-container>
  <login v-else/>
</div>
</template>
<script>
import logomicrosoft from "@/components/azure/logomicrosoft";
import login from "@/components/azure/login";
export default {
  data(){
    return{
       steps: [
          {
            target: '#v-step-0',  // We're using document.querySelector() under the hood
            content: `Ahora Logueate en tu cuenta`
          }
      ],
      login:true
    }
  },
  components:{
    logomicrosoft,
    login
  },
    mounted(){
      setTimeout(()=>{
        this.$tours['login'].start()
      },2000);
    },
    methods:{
      changeBackground(){
        login=false
        this.$emit("cb",true);
        }
    }
}
</script>
