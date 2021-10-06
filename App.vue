<template>
<h2>Employee Details</h2>
<hr/>
  <div>
    <pre>
    <!-- {{JSON.stringify(formValues,null)}} -->
    
  </pre>
  
  </div>
  <div>
  <h2 v-for="(item, index) in items" :key="item.name">
    {{ index }} {{ item }}
  </h2>
  </div>
  <button @click="deletehandler">Delete</button>
  <hr />
  <form>
    <div>
      <div>
      <input
        type="text"
        id="name"
        placeholder="Full Name"
        v-model.trim="formValues.name"
        required
      />
      </div>
<div>
      <input
        type="text"
        id="Job"
        placeholder="Job Description"
        v-model.trim="formValues.job"
        required
      />
      </div>
      <div>
      
      </div>
      
    </div>
  </form>
  <button @click="submitformhandler">Submit</button>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      formValues: {
        name: "",
        job: "",
      },

      items: [
        { name: "Aayush", job: "Analyst" },
        { name: "Soni", job: "Hostess" },
        { name: "Bipin", job: "Trainer" },
        { name: "Rajat", job: "Cricketer" },
      ],
    };
  },
  methods: {
    submitformhandler(event) {
      var itemarray = this.items.push({
        name: this.formValues.name,
        job: this.formValues.job,
      });
      event.preventDefault();

      this.formValues.name = "";
      this.formValues.job = "";
      return itemarray;
    },

    deletehandler(rowindex) {
      return this.items.splice(rowindex, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
}
</style>
