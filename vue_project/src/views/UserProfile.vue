<template id="gray">
  <body >
    <div id="app">
        <div class= "user-profile_user-panel">
            <div>
                <h2>{{fullname}}</h2>
                <div class="admin-badge" v-if="user.isAdmin">Admin</div>
                <div class="admin-badge" v-if="!user.isAdmin">Student</div>
                <div id="followerCount">Follower count : {{follower}} 
                    <button id="addButton" @click= "add_follow_user">follow</button> 
                    <button id="removeButton" @click="remove_follow_user">unfollow</button>
                </div>
            </div>
        </div>
        <div class="user-profile__twppts-wrapper">
            <TweetItem v-for="tweet in user.tweets" :key="tweet.id" :username="user.username" :tweet="tweet" />
        </div>
        <!-- <div v-for="tweet in user.tweets" :key="tweet.id">
            {{tweet.content}}
        </div> -->
    </div>
  </body>
</template>

<script>
import TweetItem from "./TweetItem.vue"
export default {
    name:"MyApp",
    components: {TweetItem},
    data() {
        return{
        follower:0,
        user:{
            id:1,
            username: 'Domingo123456',
            first_name: "Domingo",
            last_name: "Tsao",
            email:'domingo0204@gmail.com',
            isAdmin: true,
            tweets:[
                {id:1, content:"Hello worlds !!"},
                {id:2, content:"Amazing for loop in Vue !"},
            ],
                
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

<style >

body{
    display: flex;
    flex-direction: columns ;
    text-align: center;
}

button{
  border-radius: 7px;  
  font-weight: 550 ;
  flex-direction: columns ;
}
#followerCount{
    top:10px;
    right:25px;

}
#addButton{
    bottom: 2px;
    background-color: rgb(120, 190, 98);
    margin: 3px;
    /* margin-top: 10px; */
    margin-right:5px;
}
#removeButton{
    bottom: 2px;
    background-color: rgb(228, 100, 100);
}

#app{
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
  text-align: center;
  /* display:flex; */
  /* flex-direction: column; */
}

.center {
text-align: center;
}

.user-profile_user-panel{
    display: flex;
    flex-direction: column;
    font-weight:550;
    font-size: 20px;
    width: 400px;
    height: 150px;
    padding:20px;
    margin-top: 3px;
    background-color:rgb(255, 255, 255);
    border-radius: 5px;
    border: 1px solid #a2a7ad
}
.admin-badge{
    font-size: 8px;
    top:  -50%;
    right:   -15px ;
    color: white;
    background-color: rgb(110, 74, 168);
    margin: auto;
    padding: 3px;
    padding-left: 5px;
    padding-right: 5px;
    border-radius: 5px;
}
</style>