<template>
<v-app> 
    <v-navigation-drawer 
        v-model="drawer"
        permanent
        :rail="rail"
        
      >
        <template v-slot:prepend>
          <v-list-item
            lines="two"
            prepend-avatar="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTDI6q1Z4xEdxhNDRQnmepQb-VRSJMwAmkSWg&s"
            subtitle="Logged in"
            title="Jai"
          ></v-list-item>

        </template>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item prepend-icon="mdi-home-city" title="Home" value="home"></v-list-item>
          <v-list-item prepend-icon="mdi-account" title="My Account" value="account"></v-list-item>
          <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users"></v-list-item>
          <v-list-item prepend-icon="mdi-account-group-outline" title="Prelim" value="prelim" to="/prelim"></v-list-item>
          <v-list-item prepend-icon="mdi-account-group-outline" title="Remedial" value="remedial" to="/remedial"></v-list-item>
          

        </v-list>
      </v-navigation-drawer>

      <v-app-bar :elevation="2">
  <template v-slot:prepend>
    <v-app-bar-nav-icon @click.stop="rail = !rail"></v-app-bar-nav-icon>
  </template>

  <v-app-bar-title>Application Bar</v-app-bar-title>
</v-app-bar>
    <v-main>
        <v-container fluid>
            <slot />
        </v-container>
    </v-main>
</v-app>

</template>

<script  setup>
const drawer = ref(true)
const rail = ref(true)

</script>

<style>

</style>