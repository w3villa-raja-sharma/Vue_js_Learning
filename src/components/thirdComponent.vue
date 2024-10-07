<template>
  <div>
    <h1>Get input fied value TWO WAY BINDING</h1>
    <input type="text" placeholder="Enter Email" v-model="email" />
    <br />
    <input type="password" placeholder="Enter password" v-model="password"/>

    <br />
    <button type="button">Get values</button>
  </div>
</template>

<script>
export default {
  name: "thirdComponent",
  data() {
    return {
       email: null,
       password:null,
    }
  },
  methods:{
    getData()
    {
      console.warn("values : ",this.email,this.password)
    }
  }
};
</script>
