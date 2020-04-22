<template lang="html">

  <div class="tweet-list-item">
  <div class="row">
    <div class="usr-img-container">
      <img class="user-image" v-bind:src="tweet.img" alt="">
    </div>
    <div class="usr-twt-container">
      <span class="user-name">{{tweet.name}} </span>
      <span class="user-handle">{{tweet.handle}}</span>
      <p>{{tweet.tweet}}</p>
    </div>
  </div>
  <div class="usr-likes-container">
    <div class="row">
      <div class="icon-space"></div>
      <div class="icons">
        <p><img class="icon-img-comment" src="../assets/comment.png"></p>
      </div>
      <div class="icons">
        <p><button class="retweet-button" v-on:click="tweet.retweets += 1"><img class="icon-img-retweet" src="../assets/retweet.png" alt=""></button>{{tweet.retweets}}</p>
      </div>
      <div class="icons">
        <p><button class="like-button" v-on:click="tweet.likes += 1"><img class="icon-img-like" src="../assets/like.png" alt=""></button>{{tweet.likes}}</p>
      </div>
    </div>
  </div>
</div>

</template>

<script>
export default {
  name: 'tweet-list-item',
  props: ['tweet']
}
</script>

<style lang="css" scoped>

.row:after {
  content: "";
  display: table;
  clear: both;
}

.usr-img-container {
  /* border-style: solid; */
  float: left;
  width: 15%;
  margin-top: 6px;
  padding-top: 8px;
  padding-left: 15px;
}

.user-image {
  height: 60px;
  border-radius: 50%;
}

.usr-twt-container{
  /* border-style: solid; */
  float: left;
  width: 75%;
  margin-top: 6px;
  padding-top: 8px;
  padding-left: 8px;
  clear: none;
  word-wrap: break-word;
}

.user-name {
  font-weight: 700;
}

.user-handle {
  color: #8C9AA6;
}

.usr-likes-container {
  /* border-style: solid; */
  height: 35px;
  color: #8C9AA6;
}

.icon-space {
  /* border-style: solid; */
  width: 17%;
  height: 25px;
  text-align: left;
  float: left;
}

.icons {
  /* border-style: solid; */
  width: 20%;
  height: 25px;
  text-align: left;
  float: left;
}

.icon-img-comment {
  height: 18px;
  margin-left: 10px;
}

.icon-img-retweet {
  height: 18px;
  margin-right: 10px;
}

.icon-img-retweet:hover {
  background-color: #EAF5FE;
}

.icon-img-like {
  height: 18px;
  margin-right: 10px;

}

.icon-img-like:hover {
  background-color: #EAF5FE;
}

p {
  margin-top: 4px;
}

button {
  background: none;
  border: none;
  padding: 0;
  margin: 0;
  border-radius: 50%;
}

button:focus {
  outline: none;
}


</style>
