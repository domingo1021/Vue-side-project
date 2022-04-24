<template>
  <header>
    <img alt="Vue logo" class="center" src="@/assets/logo.svg" width="125" height="125" />
  </header>
  <footer><div id="app">{{copywrite}} owned by - {{fullname}} <p>Follower count : {{follower}} <button id="addButton" @click="add_follow_user">follow</button> <button @click="remove_follow_user">unfollow</button></p> </div></footer>
</template>

<script>
// import { RouterLink, RouterView } from 'vue-router'
import HomeView from "./views/HomeView.vue"
export default{
  name: "MyApp", 
  components:HomeView,
  data() {
    return{
      copywrite: "@Copywrite ",
      follower:0,
      user:{
        id:1,
        username: 'user_1',
        first_name: "Domingo",
        last_name: "Tsao",
        email:'domingo0204@gmail.com',
        isAdmin: true,
      }
    }
  },
  watch: {
    follower(newFollowersCount, oldFollowersCount){
      if(oldFollowersCount < newFollowersCount){
        console.log("Weee!!! new follower in !");
      }else if (newFollowersCount < oldFollowersCount){
        console.log("Awww.. follower out :( ")
      }
    }
  },
  computed:{
    fullname(){
      return  `${this.user.first_name} ${this.user.last_name}`;
    }
  },
  methods:{
    add_follow_user(){
      this.follower++;
    },
    remove_follow_user(){
      if(this.follower>0){
        this.follower--;
      }
    }
  },
  mounted(){
    alert("welcome !");
  }
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
#addButton{
  margin:10px;
}
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}
</style>
