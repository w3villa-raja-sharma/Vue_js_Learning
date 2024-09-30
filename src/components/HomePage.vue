<template>
<div>
   <h1>Props in vue js</h1>  
   <StudentDetails name='Rakshit' />
   <TeacherDetails name='ShreeNath sir' />
</div>
</template>

<script>

import StudentDetails from './StudentDetails.vue'
import TeacherDetails from './TeacherDetails.vue'

export default {
    name: 'HomePage',

    components: {
        StudentDetails,
        TeacherDetails
    }
}
</script>


<style scoped>
h1{
    color:brown;
    font-weight: 200;
}
</style>
