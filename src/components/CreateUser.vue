<template>
  <div class= "container">
    <form @submit="onSubmit" >
      <label><span >Login ID  </span>
        <input type="text" class="input" placeholder=" " v-model="data.form.login_ID"></label>
      <label><span >Name </span>
        <input type="text" class="input" placeholder=" " v-model="data.form.name"></label>

      <div>
        <label>Department</label>
        <select id = "department" name="department" @change="onChange($event)" class="form-select form-control"  v-model="data.form.departement">
          <option>---- Select Department ----</option>
          <option value="Portfolio Management">Portfolio Management</option>
          <option value="Trading">Trading</option>
          <option value="Compliance">Compliance</option>
          <option value="Technology">Technology</option>
          <option value="Business Development">Business Development</option>
          <option value="Human Resources">Human Resources</option>
        </select>

      </div>
      <label for="toggle_button">
        <span>Is Manager?</span>
        <input type="checkbox" id="toggle_button" v-model="data.form.is_Manager">
        <span class="toggle__switch"></span>
      </label>
      <b-form-select v-model="data.form.department" :options="options"></b-form-select>
      <label for="hire_date">Hire Date
        <input id = "hire_date" type="date" class="input"  v-model="data.form.hire_date" ></label>
      <div></div>
      <input type="submit" class="button is-info"  value="Save"  >
    </form>
    <input type="button" class="btn" @click="resetForm()" value="Clear Form">
  </div>
</template>

<script>

export default {
  data () {
    return {
      data: {
        form: {
          seen: true,
          login_ID: '',
          name: '',
          department: '',
          is_Manager: false,
          hire_date: new Date().toISOString().substr(0, 10) // 05/09/2019,
        }
      }
    }
  },
  methods: {
    onSubmit: function () {
      console.log('Make API request.')
      if (!this.data.form.login_ID) {
        alert('ID must be 10 chars or less')
        return
      }

      if (!this.data.form.name) {
        alert('Name must be provided and must be 100 characters or less')
        return
      }

      if (!this.data.form.department) {
        alert('Please select a department')
        return
      }
      this.resetForm() // clear form automatically after successful request
    },
    resetForm () {
      console.log('Reseting the form')
      var self = this // you need this because *this* will refer to Object.keys below`

      // Iterate through each object field, key is name of the object field`
      Object.keys(this.data.form).forEach(function (key, index) {
        self.data.form[key] = ''
      })
    }
  }
}
</script>
<style scoped>
@media screen and (min-width: 768px) {
form {
display: flex;
flex-direction: column;
flex-wrap: wrap;
justify-content: space-between;
align-content: space-evenly;
}

form input {
width: 200px;
box-sizing: border-box;
padding: 10px 20px;
float: right;
}
form label {
width: auto;
box-sizing: border-box;
align-content: space-evenly;
justify-content: right;
float: left;
border-radius: 5px;
}

.container {
max-width: 500px;
margin: 30px auto;
overflow: auto;
min-height: 300px;
border: 1px solid steelblue;
padding: 30px;
border-radius: 5px;
}

.btn {
display: inline-block;
background: #2c3e50;
color: #fff;
border: none;
padding: 10px 20px;
margin: 5px;
border-radius: 5px;
cursor: pointer;
text-decoration: none;
font-size: 15px;
font-family: inherit;
}

.btn:focus {
outline: none;
}

.btn:active {
transform: scale(0.98);
}

.btn-block {
display: block;
width: 100%;
}

input {
border: #2c3e50;
outline: none;
border-bottom: 1px solid #ddd;
font-size: 1em;
padding: 5px 0;
margin: 10px 0 5px 0;
width: 100%;
}

button {
background-color: #3498db;
padding: 10px 20px;
margin-top: 10px;
border: none;
color: white;
}
}
</style>
