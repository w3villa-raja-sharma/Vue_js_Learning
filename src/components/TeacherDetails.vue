<template>
<div>
    <h2>IIT BOMBAY Teacher Details </h2>
    <h4> Teacher Name is : {{name}} </h4>
</div>
</template>

<script>

export default {
    name:'TeacherDetails',
    props:{
        name: String
    }
}
</script>
