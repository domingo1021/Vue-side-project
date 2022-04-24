<template>
  <header>
    <img alt="Vue logo" class="center" src="@/assets/logo.svg" width="125" height="125" />
  </header>
  <body v-cloak>
    <UserProfile />
  </body>
  <footer v-cloak>
    <div>&copy;Copywrite 2022 - Domingo Tsao </div>
    <br>
    <br>
  </footer>
</template>

<script>
import UserProfile from "./views/UserProfile.vue"
export default{
  name: "MyApp", 
  components:{UserProfile},
}
</script>

<style>
@import '@/assets/base.css';

#app{
  /* max-width: 1280p/x; */
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
  text-align: center;
  display:flex;
  flex-direction: column;
}

div{
    display:inline;
}

[v-cloak] {
  display: none;
}
</style>
