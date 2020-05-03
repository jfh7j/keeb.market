<template>  
  <fragment id="post">
    <tr style="background-color: #efeddf; border-top: 10px solid white">
        <th> {{category}} </th>
        <td> {{country}} </td>
        <td> <a v-bind:href="'https://reddit.com/u/' + poster"> {{poster}} </a> </td>
        <td> <a v-bind:href="link">{{items}}</a></td>
        <td> {{payment}} </td>
        <td> {{date}} </td>
    </tr>
    <tr>
      <td colspan="6" style="border-top: none; border-bottom: none; background-color: #fefdef">
        {{description}}
      </td>
    </tr>
  </fragment>

</template>

<script>
import { Fragment } from 'vue-fragment';

export default {
  name: 'Post',
  components: {
    Fragment
  },
  props: {
    category: String,
    country: String,
    poster: String,
    items: String,
    payment: String,
    date: String,
    description: String,
    link: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
