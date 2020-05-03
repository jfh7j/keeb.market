<template>
<div id="app">
  <nav-bar></nav-bar>
  <div id="mainBody">
    <search-form v-on:updateSearch="searchValue=$event"></search-form>
    <main-table :searchValue = "searchValue"></main-table>
    <h1>{{searchValue}}</h1>
  </div>
</div>
</template>

<script>
import MainTable from './components/MainTable.vue'
import NavBar from './components/NavBar.vue'
import SearchForm from './components/SearchForm.vue'

export default {
  name: 'App',
  components: {
    MainTable,
    NavBar,
    SearchForm
  },
  data () {
    return{
      searchValue: ""
    }
    
  }
}
</script>

<style>
#mainBody{
  max-width: 1140px;
  width: 100%;
  margin-right: auto;
  margin-left: auto;
}
tr{
  text-align:left;
}
</style>
