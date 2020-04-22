<template lang="html">
  <div class="twitter-container">
    <div class="twitter">

      <header class="row">
        <form class="new-tweet" v-on:submit.prevent="addTweet">
          <div class="twt-img-container">
            <img class="twitter-image" src="./assets/twitter.png">
          </div>
          <div class="twt-input-container">
            <input type="text" v-model="newTweet.tweet" placeholder="What's happening?">
            <select v-model="newTweet.handle" required>
              <option v-for="tweet in tweets">{{tweet.handle}}</option>
            </select>
            <input class="tweet-butn" type="submit" value="Tweet">
          </div>
        </form>
      </header>

      <section>
        <div class="overall-menu-container">
          <div class="explore">
            <p>Explore</p>
          </div>
          <div class="menu-container">
            <div class="row">
              <div class="top-container">
                <button class="menu-butn-unclicked" v-on:click.prevent="topLikes" type="submit">Top</button>
              </div>
              <div class="top-container">
                <button class="menu-butn-unclicked" v-on:click.prevent="latestLikes" type="submit">Latest</button>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section>
        <hr>
        <div class="tweets" v-for="tweet in filteredTweets">
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
                <p><img class="icon-img-comment" src="./assets/comment.png"></p>
              </div>
              <div class="icons">
                <p><button class="retweet-button" v-on:click="tweet.retweets += 1"><img class="icon-img-retweet" src="./assets/retweet.png" alt=""></button>{{tweet.retweets}}</p>
              </div>
              <div class="icons">
                <p><button class="like-button" v-on:click="tweet.likes += 1"><img class="icon-img-like" src="./assets/like.png" alt=""></button>{{tweet.likes}}</p>
              </div>
            </div>
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
          retweets: 10,
        },
        {
          id: 2,
          name: 'Fatima',
          handle: '@fantasticfatima',
          img: 'https://semantic-ui.com/images/avatar2/large/molly.png',
          tweet: 'Better late than never but never late is better.',
          likes: 12,
          retweets: 7
        },
        {
          id: 3,
          name: 'Xin',
          handle: '@xeroxin',
          img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
          tweet: 'Beauty in the struggle, ugliness in the success.',
          likes: 18,
          retweets: 5
        }
      ],
      newTweet: {
        id: 0,
        name: "",
        handle: "",
        img: "",
        tweet: "",
        likes: 0,
        retweets: 0
      },
      likeAmount: 0
    }
  },
  computed: {
    filteredTweets: function () {
      return this.tweets.filter((tweet) => {
        return tweet.likes >= this.likeAmount;
      });
    },
  },
  methods: {
    topLikes: function () {
      this.likeAmount = 11;
    },
    latestLikes: function () {
      this.likeAmount = 0;
    },
    addTweet: function () {

      const handle = this.newTweet.handle;
      const tweetObject = this.tweets.find(tweet => tweet.handle === handle);

      this.newTweet.id = tweetObject.id;
      this.newTweet.name = tweetObject.name;
      this.newTweet.img = tweetObject.img;

      this.tweets.unshift(this.newTweet);

      this.newTweet = {
        id: 0,
        name: "",
        handle: "",
        img: "",
        tweet: "",
        likes: 0,
      }
    }

  }
}
</script>




<style lang="css" scoped>

.twitter-container {
  /* border-style: solid; */
  display: block;
  text-align: center;
  height: 100vh;
}

.twitter {
  /* border-style: solid; */
  display: inline-block;
  text-align: left;
  width: auto;
  border: solid 2px #E6ECF0;
  height: 100vh;
  border-radius: 5%;
}

.row:after {
  content: "";
  display: table;
  clear: both;
}



/* FORM  */

form.new-tweet {
  width: 500px;
  max-width: 500px;
}

.twt-img-container {
  /* border-style: solid; */
  float: left;
  width: 10%;
  height: 34px;
  margin-top: 6px;
  padding-top: 5px;
  text-align: right;
}

.twitter-image {
  height: 35px;
}

.twt-input-container {
  /* border-style: solid; */
  float: right;
  width: 85%;
  height: 34px;
  margin-top: 6px;
  padding-top: 10px;
  clear: none;
}

input[type=text] {
  border-radius: 15%;
  background-color: #E6ECF0;
  color: #8C9AA6;
  font-weight: bold;
  font-size: 15px;
  width: 310px;
  height: 18px;
  display: inline-block;
  margin-right: 15px;
}

select {
  width: 10px;
  margin-right: 15px;
}

.tweet-butn {
  border-radius: 15%;
  font-size: 15px;
  background-color: #00acee;
  color: #fff;
}

.tweet-butn:focus {
  outline: none;
}

/* FORM END  */



/* MENU */

.overall-menu-container {
  /* border-style: solid; */
  padding-top: 10px;

}

.menu-container {
  /* border-style: solid; */
  display: block;
  text-align: center;
}

.explore {
  /* border-style: solid; */
  width: 60px;
  height: 30px;
  margin-left: 37px;
  font-weight: 700;
  font-size: 18px;
}

.top-container {
  width: 20%;
  height: 20px;

  /* border-style: solid; */
  padding-top: 5px;
  margin: 0;
  display: inline-block;
}

.menu-butn-unclicked {
  font-size: 22px;
  color: #8C9AA6;
  padding-top: 20px;
  padding-right: 10px;
  padding-left: 10px;
  padding-bottom: 10px;
  /* border-style: solid; */
  border-radius: 0%;
}

.menu-butn-unclicked:hover {
    background-color: #EAF5FE;
    color: #00acee;
}



/* .menu-butn-clicked {
font-size: 18px;
color: #00acee;
} */

/* MENU END  */



/* TWEETS */

.tweets {
  border: solid 1px #E6ECF0;
  width: 500px;
  max-width: 500px;
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

/* TWEETS END */

hr {
  padding: 0;
  margin-top: 10px;
}
</style>



<style>
body {
  font-family: system-ui;
}
</style>
