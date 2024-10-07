<template>
  <div>
    <h1>Props in vue js</h1>
    <StudentDetails name="Rakshit" />
    <StudentDetails :name="name" />
    <TeacherDetails name="ShreeNath sir" />

    <h1>Send Data CHILD to PARESNT in vue js</h1>
    <h3>{{ childUser }}</h3>
    <ChildComp :getUser="getUserName" />

    <h1>Ref in vue js</h1>
    <input type="text" ref="input" />
    <button v-on:click="getData">click me</button>

    <h1>Form in vue js</h1>
    <ul>
      <li v-for="item in error" v-bind:key="item">{{item}} not valid</li>
    </ul>
    <form>
      <label>Email : </label>
      <input type="text" placeholder="Enter the Email" v-model="form.email" />
      <br />
      <br />
      <label>Password : </label>
      <input
        type="password"
        placeholder="Enter the Password"
        v-model="form.password"
      />
      <br />
      <br />
      <h4> Country </h4>
      <select v-model="form.country">
        <option>India</option>
        <option>USA</option>
        <option>Australia</option>
        <option>Nether Land</option>
        <option>Austria</option>
      </select>
       <br />
      <br />
      <h4> Technology </h4>
        <label> Java </label>
        <input type="checkbox" value="Java"  v-model="form.technology" />
        <label> SpringBoot </label>
        <input type="checkbox" value="SpringBoot" v-model="form.technology" />

         <h4> Gender </h4>
        <label> Male </label>
        <input type="radio" value="male"  name="gender" v-model="form.gender" />
        <label> female </label>
        <input type="radio" value="female" name="gender" v-model="form.gender" />

      <button v-on:click="login" type="button">Log In</button>
    </form>

    <thirdComponent />

    <h1>Form Modifiers</h1>
    <input type="text" v-model="c_data" />
    <!-- <input type="text" v-model.lazy="c_data" /> -->
    <!-- <input type="text" v-model.trim="c_data" /> -->
    <!-- <input type="Number" v-model.number="c_data" /> -->
    <!-- <h3>Company Name is :- {{ typeof(c_data) }}</h3> -->
    <h3>Company Name is :- {{ c_data }}</h3>

    <h1>Non Props Data</h1>
    <user data="Samarth" id="user-cmp" />

   <h1>Computed Property</h1>
     <h3>{{(dollars*rupeeVal)-discount}}</h3>  // Normal
     <h3>{{getResult}}</h3> // computed property
     <h3>{{getResultMethod()}}</h3> // computed property
     

   <h1>Watchers</h1>
   <h3>{{count}}</h3>
   <button v-on:click="count=count+1"> + </button>
   <br />
   <button v-on:click="count=count-1"> - </button>

   <h1> Slots in vue js</h1>
   

   <childslot>
      <template v-slot:header>
        <h3>  Learning vue js document</h3>
      </template>
    <template v-slot:content>
      <h3> slots and multiple slots</h3>
    </template>
   </childslot>
   
  <h1>DYNAMIC COMPONENT</h1>

  <button @clicl="tab='Java'">Load Java</button>
  <button @click="tab='Node'">Load Node</button>
  <button @click="tab='Php'">Load Php</button>

  <component :is="tab" />
<!-- <Java />
<Node />
<Php /> -->
   
  </div>
</template>

<script>
import StudentDetails from "./StudentDetails.vue";
import TeacherDetails from "./TeacherDetails.vue";
import ChildComp from "./ChildComp.vue";
import thirdComponent from "./thirdComponent.vue";
import user from "./user.vue";
import Childslot from "./Childslot.vue";
import Java from "./Java.vue";
import Node from "./Node.vue";
import Php from "./Php.vue";
export default {
  name: "HomePage",
  data() {
    return {
      name: " Aakriti Goel",
      childUser: "",
      form: 
      {
        email: "",
        password: "",
        country: "",
        technology: [],
        gender: "",
      },
      error: [],
      
      c_data:"",

      dollars: 100,
      rupeeVal: 60,
      discount:10,

      count:0,

      tab:'Java'
    };
   
  },
   watch: {
      count() {
       alert("Value changed")
      }
    },
  computed: {
     getResult() {
       return (this.dollars * this.rupeeVal)-this.discount;
     }
  },
  components: {
    StudentDetails,
    TeacherDetails,
    ChildComp,
    thirdComponent,
    user,
    Childslot,
    Java,
    Node,
    Php
  },
  methods: {
    getResultMethod() {
       return (this.dollars * this.rupeeVal)-this.discount;
     },
    getUserName(name) {
      alert(name);
      this.childUser = name;
    },
    getData() {
      this.$refs.input.focus();

      let val = this.$refs.input.value;
      console.warn(val);
      this.$refs.input.style.color = "red";
    },
    login() {
      this.error =[];
      // console.warn("login data", this.form);
      for(const item in this.form)
      {
        if(this.form[item]==="" || this.form[item].length===0)
        {
          this.error.push(item) 
        }
      }
      if(this.error.length===0)
      {
        alert("Data ha been submmitted")
      }
      console.warn("login data", this.form,this.error);
    },
  },
};
</script>


<style scoped>
h1 {
  color: brown;
  font-weight: 200;
}
/* form styling */
body {
  font-family: Arial, sans-serif;
  background-color: #f0f2f5;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

form {
  background-color: #fff;
  padding: 30px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 300px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}

input[type="text"],
input[type="password"],
select {
  width: 100%;
  padding: 8px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

input[type="checkbox"],
input[type="radio"] {
  margin-right: 5px;
}

h4 {
  margin-bottom: 10px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}


</style>
