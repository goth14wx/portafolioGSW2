<template>
 <v-sheet
    height="400"
    class="overflow-hidden white"
    style="position: relative;"
  >
    <v-container class="fill-height">
     <v-row>
        <v-col cols="12" sm="3">
        </v-col>
       <v-col cols="12" sm="3" :self-align="'center'">
           <v-card
           class=""
    max-width="300"
    tile
  >
    <v-list dense light tile depressed  v-if="azureMarket">
      <v-subheader class="black--text">Azure Marketplace</v-subheader>
      <v-list-item-group v-model="item" color="primary" >
        <v-list-item
          v-for="(item, i) in itemsList"
          :key="i"
        >
          <v-list-item-icon>
            <v-icon v-text="item.icon"></v-icon>
          </v-list-item-icon>
          <v-list-item-content id="v-step-1">
            <v-list-item-title @click="resources=true" v-text="item.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>


  </v-card>
       </v-col>
       <v-col sm="3">
 <v-list dense light tile depressed v-if="resources" >
      <v-subheader class="black--text">Popular</v-subheader>
      <v-list-item-group v-model="itemP" color="primary">
        <v-list-item
          v-for="(item, i) in itemsListPopular"
          :key="i"
        >
          <v-list-item-icon>
            <v-icon v-text="item.icon"></v-icon>
          </v-list-item-icon>
          <v-list-item-content  id="v-step-2">
            <v-list-item-title v-text="item.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
       </v-col>
     </v-row>
    </v-container>

    <v-navigation-drawer
      absolute
      permanent
      light
      color="#f8f8f8"
      fixed
    >

      <v-list >

        <v-list-item
          v-for="item in items"
          :key="item.title"
          link

        >
          <v-list-item-icon>
            <v-icon  class="green--text">{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content id="v-step-0" @click="azureMarket=true">
            <v-list-item-title >{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
       <v-tour name="dashboard" :steps="steps"></v-tour>
    </v-navigation-drawer >

  </v-sheet>
</template>
<script>
  export default {
    data () {
      return {
        azureMarket:false,
        resources:false,
        items: [
          { title: 'create a resource', icon: 'add' },
        ],
         item: 0,
         itemP:2,
      itemsList: [
        { text: 'get started', icon: 'mdi-clock' },
        { text: 'Recently created', icon: 'mdi-account' },
        { text: 'AI + Machine Learning', icon: 'mdi-flag' },
      ],
       itemsListPopular: [
        { text: 'Windows Server 2016 Datacenter', icon: 'view_module' },
        { text: 'Web App', icon: 'public' },
        { text: 'SQL Database', icon: 'dns' },
      ],
      steps: [
          {
            target: '#v-step-0',  // We're using document.querySelector() under the hood
            content: `Crea un nuevo resource`
          },
            {
            target: '#v-step-1',  // We're using document.querySelector() under the hood
            content: `Selecciona get started`
          }
          ,
            {
            target: '#v-step-2',  // We're using document.querySelector() under the hood
            content: `Selecciona SQL DATABASE`
          }
      ],
      }
    },
    mounted(){
      setTimeout(()=>{
        this.$tours['dashboard'].start()
      },1000)
    },
  }
</script>
