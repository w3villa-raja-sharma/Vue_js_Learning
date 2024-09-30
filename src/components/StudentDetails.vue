<template>
<div>
    <h2>IIT BOMBAY Student Details :- </h2>
    <h4> Student Name is : {{name}} </h4>
</div>
</template>

<script>

export default {
    name: 'StudentDetails',
    props:{
        name:String
    }
}
</script>
