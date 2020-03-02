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
 

        <v-btn text>Forum</v-btn>

        <v-btn text>Ask Question</v-btn>

        <v-btn text>Category</v-btn>

    <router-link to="/login">
        <v-btn text>Login</v-btn>
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
    
}
</script>

<style>
    
</style>

