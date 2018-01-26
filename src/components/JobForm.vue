 <template>
  <div id="JobForm">
      <aside id="side-bar">
        <h3>Add a Job</h3>
        <form v-on:submit.prevent= "submitForm" method= "POST" class="job-form">
          <label for="title">Title</label>
          <input v-model= "job.title" type="text" name="title">
          <label for="pay">Compensation</label>
          <input v-model = "job.pay" type="text" name="pay">
          <label for="description">Description</label>
          <textarea v-model = "job.description" name="description" rows="8" cols="40"></textarea>
          <input type="submit" name="submit" value="Submit" />
        </form>
    </aside>
  </div>
</template>
<script>
export default {
  name: "JobForm",
  props: ["postListing"],
  data(){
      return {job:{
          title:"", 
          pay:"", 
          description:"",
          interested: []
        }
      }
    },
methods:{
    submitForm(){
        this.postListing(this.job) 
        this.job = {
            title:"" , 
            pay:"", 
            description:"", 
            interested:[]
            }
     }
    }       
}
</script>
<style scoped>
#JobForm {
  grid-column: 4/5;
}

form {
  display: flex;
  flex-flow: column;
  justify-content: space-around;
}
</style>
