<template lang="html">
  <div class="twitter-container">
    <div class="twitter">
      <header>
        <span>
          <div class="twt-img-container">
            <img class="twitter-image" src="./assets/twitter.png" alt="">
          </div>
          <div class="twt-input-container">
            <input type="text" name="" value="" placeholder="What's happening?">
          </div>
        </span>
      </header>
      <section>
        <div class="tweets" v-for="tweet in tweets">
          <div class="usr-img-container">
            <img class="user-image" v-bind:src="tweet.img" alt="">
          </div>
          <div class="usr-twt-container">
            <span class="user-name">{{tweet.name}} </span>
            <span class="user-handle">{{tweet.handle}}</span>
            <p>{{tweet.tweet}}</p>
          </div>
          <div class="usr-likes-container">
            <p>{{tweet.likes}}</p>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      tweets:[
        {
          id: 1,
          name: 'James',
          handle: '@jokerjames',
          img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
          tweet: "If you don't succeed, dust yourself off and try again.",
          likes: 10,
        },
        {
          id: 2,
          name: 'Fatima',
          handle: '@fantasticfatima',
          img: 'https://semantic-ui.com/images/avatar2/large/molly.png',
          tweet: 'Better late than never but never late is better.',
          likes: 12,
        },
        {
          id: 3,
          name: 'Xin',
          handle: '@xeroxin',
          img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
          tweet: 'Beauty in the struggle, ugliness in the success.',
          likes: 18,
        }
      ]
    }
  }
}
</script>

<style lang="css" scoped>

.twitter-container {
  border-style: solid;
  display: block;
  text-align: center;
  height: 100vh;
}

.twitter {
  border-style: solid;
  display: inline-block;
  text-align: left;
}

.twt-img-container {
  border-style: solid;
}

.twt-input-container {
  border-style: solid;
}

.usr-img-container {
  border-style: solid;
}

.usr-twt-container{
  border-style: solid;
}

.usr-likes-container {
  border-style: solid;
}


.twitter-image {
  height: 30px;
}

input[type=text] {
  border-radius: 25%;
  background-color: #E6ECF0;
  color: #8C9AA6;
  font-weight: bold;
  width: 300px;
}

.tweets {
  border: solid 1px #E6ECF0;
}

.user-image {
  height: 60px;
  border-radius: 50%;
}

.user-name {
  font-weight: 700;
}

.user-handle {
  color: #8C9AA6;
}

</style>

<style>
body {
  font-family: system-ui;
}
</style>
