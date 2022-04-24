<template>
  <div class="tweet-item">
    <div class="user-profile__tweet">
      <div class="tweet-item">
        @{{ username }}: {{ tweet.content }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TweetItem",
  props: {
    username: {
      type: String,
      required: true
    },
    tweet: {
      type: Object,
      required: true
    }
  }
};
</script>

<style>
.tweet-item{
  display: flex;
  flex-direction: column;
  text-align: center;
}
</style>