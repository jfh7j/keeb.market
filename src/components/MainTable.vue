<template>
  <div class="MainTable">
    <table class="table small" style="width: 100%; min-width: 750px">
        <thead>
            <tr>
                <th>Category</th>
                <th>Country</th>
                <th>Poster</th>
                <th>Item(s)</th>
                <th>Payment</th>
                <th>Date</th>
            </tr>
        </thead>
        
        <tbody>
          <post
            v-for="post in posts"
            v-bind:key="post.name"
            v-bind:items="post.title"
            v-bind:description="post.selftext"
            v-bind:link="post.url"
            v-bind:category="post.link_flair_css_class"
            v-bind:country="post.title.substr(post.title.indexOf('[')+1, post.title.indexOf(']')-1)"
            v-bind:poster="post.author.name"
            v-bind:payment="post.link_flair_css_class == 'buying' ? post.title.substr(post.title.indexOf('[H]') + 3, post.title.indexOf('[W]') - 11) : post.title.substr(post.title.indexOf('[W]') + 3, post.title.length-1)"
            v-bind:date="getTimeAgo(new Date(post.created_utc * 1000))"
          ></post>
        </tbody>
    </table>
</div>
</template>
<script>
//https://not-an-aardvark.github.io/reddit-oauth-helper/
import Post from "./Post.vue";
import TimeAgo from 'javascript-time-ago';
import en from 'javascript-time-ago/locale/en';
TimeAgo.addLocale(en);
const snoowrap = require("snoowrap");
const r = new snoowrap({
  userAgent:"jfh7j",
  clientId: "oNx4homoSbka6w",
  clientSecret: "DKdbEZd-SogWV84RoXS0mmzTreg",
  refreshToken: "13733312036-Q4z-6ItricuLRBssqulIfQsGOoE"
})
export default {
  name: 'MainTable',
  components: {
    Post
  },
  props: {
    searchValue: String
  },
  data () {
    return {
      posts: [],
    }
  },
	mounted() {
		this.getPosts();
  },
  watch: {
    searchValue: function () {
      this.getPosts();
    }
  },
  methods: {
    async getPosts() {
      const subreddit = await r.getSubreddit('mechmarket');
      this.posts = await subreddit.getNew({limit: 20});
      console.log(this.posts);
    },
    getTimeAgo(d){
      const timeAgo = new TimeAgo('en-US');
      return timeAgo.format(d);
    }
  }
}
</script>

