<template>
  <v-card class="overflow-hidden">
    <v-app-bar
      absolute
      color="white"
      elevate-on-scroll
      scroll-target="#scrolling-techniques-7"
    >
      <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon> -->
 
      <v-toolbar-title>BitFumes</v-toolbar-title>
 
      <v-spacer></v-spacer>
      <router-link 
      v-for="item in items"
      :key="item.title"
      :to="item.to"
      v-if="item.show"
      >
          <v-btn text>{{ item.title }}</v-btn>
      </router-link>
    </v-app-bar>
    <v-sheet
      id="scrolling-techniques-7"
      class="overflow-y-auto"
      max-height="600"
    >
      <v-container style="height: 60px;">
 
      </v-container>
    </v-sheet>
  </v-card>
</template> 


<script>
export default {
    data(){
      return {
        items: [
          {title : 'Forum', to:'/forum',show:true},
          {title : 'Ask Question', to:'/ask',show:User.loggedIn()},
          {title : 'Category', to:'/category',show:User.loggedIn()},
          {title : 'Logout', to:'/logout',show:User.loggedIn()},
          {title : 'Login', to:'/login',show: !User.loggedIn()},


        ]
      }
    },
    created(){
      EventBus.$on('logout', () => {
          User.logout()
      })
    }
}
</script>

<style>
    
</style>

