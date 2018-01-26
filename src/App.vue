<template>
  <div id="app">
    <TheHeader/>
    <main>
      <JobList  id="job-list" v-bind:jobListData="listingData"/>
      <JobForm v-bind:postListing="addListing"/>
    </main>
    <TheFooter/>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader"
import TheFooter from "./components/TheFooter"
import JobList from "./components/JobList"
import JobForm from "./components/JobForm"

export default {
  name: 'App',
  components: {
    TheHeader, TheFooter, JobList, JobForm
  },
    methods: {
      getListings() {
        fetch(this.apiURL)
          .then(response => response.json())
          .then(response => {
            this.listingData = response.reverse()
            console.log(this.listingData)
          })
      },
      addListing(listing){
        this.listingData.unshift(listing)
      }
  },
  data(){
    return{
      apiURL: "../static/listings.json",
      listingData: []
    }
  },
  mounted(){
    this.getListings();
  }
}
</script>

<style>
html {
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin: 0 30px 0 30px;
  padding: 0;
  font-family: sans-serif;
  color: #1B997A;
  display: grid;
  grid-template-rows: 15% 75% 10%;
}

main {
  grid-row: 2/3;
  display: grid;
  grid-template-columns: 5% 42.5% 5% 42.5% 5%;
}

#job-list {
  grid-column: 2/3;
}
</style>