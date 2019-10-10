<template>
    <v-content >
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="8"
            md="4"
          >
            <v-card class="mt-12 pa-5" light tile >
              <v-toolbar
                light
                flat
              >
                <v-toolbar-title><img src="@/assets/img/microsoftLogin.png" alt="">

                </v-toolbar-title>
                <div class="flex-grow-1"></div>

              </v-toolbar>
              <v-card-text>
                 <h2><strong class="black--text font-maven">Sign in</strong></h2>
                <v-form class="pa-5">
                    <v-tooltip right>
                  <template v-slot:activator="{ on }">

                    <div style="border-bottom:1px solid black" class="animated" :class="{'fadeOutLeft':!isMail}" >
                      <span class="correo black--text"></span>
                    </div>
                    <div style="border-bottom:1px solid black" class="animated" :class="{'fadeInRigth':isMail}">
                      <span class="password black--text"></span>
                    </div>
                  </template>

                    </v-tooltip>

                </v-form>
                <span class="black--text pt-10">No account? <a href="#">Create one!</a></span>
              </v-card-text>
              <v-card-actions>
                <div class="flex-grow-1"></div>
                <v-btn color="blue white--text" v-if="isMail" id="v-step-0" tile large elevation="0" @click="changeIsMail">Next</v-btn>
                 <v-btn color="blue white--text" v-else id="v-step-1" tile large elevation="0" @click="goto">Next</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
      <v-tour name="loginIn" :steps="steps"></v-tour>
    </v-content>
</template>

<script>
import Typed from 'typed.js';
export default {
  data(){
    return{
steps: [
          {
            target: '#v-step-0',  // We're using document.querySelector() under the hood
            content: `Ahora puedes ingresar tu contraseña`
          },
          {
            target: '#v-step-1',  // We're using document.querySelector() under the hood
            content: `Ahora puedes ingresar a tu cuenta`
          }
      ],
      isMail:true
    }
    },
    mounted(){
       new Typed('.correo', {
      strings: ["tusuario@outlook", "tusuario@catolica.edu.sv"],
      typeSpeed: 50,
      backSpeed:50
      });
        setTimeout(()=>{
        this.$tours['loginIn'].start();
      },2000);
    },
    methods:{
      changeIsMail(){
        this.isMail=false;
        new Typed('.password', {
      strings: ["*****", "*******************"],
      typeSpeed: 50,
      backSpeed:50
      });
        },
        goto(){
          this.$emit("changeNow");
        }
    }
}
</script>
