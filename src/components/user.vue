<template>
    <div>
        <h4>Manish</h4>
        <h4>Deepak</h4>
        <h4>Rohit</h4>
        <h4 v-bind="$attrs">Samad</h4> 
        <h4>{{data}}</h4>            
    </div>
</template>

<script>
export default {
    name:'user nonProp Data',
    inheritAttrs:false,
    props: {
        data: String
    }
};
</script>
