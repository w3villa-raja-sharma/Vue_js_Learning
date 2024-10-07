<template>
    <div>
        <h4>Child component</h4>
        <button v-on:click="getUser(userName)">Send user Name</button>
    </div>
</template>

<script>
export default {
   name:'ChildComp',
   data() {
    return {
        userName: "Raja"
    }
   },
   props: {
    getUser: Function
   }
}
</script>

