<script setup>
  import Button from './Button.vue';
</script>

<template>
    <header>
        <h1>{{title}}</h1>
        <Button  v-show="homePage" @btn-click="$emit('toggle-add-task')" :color="buttonName ? 'darkred' : 'green'" :text="buttonName ? 'Close' : 'Add Task'"/>
    </header>
</template>

<script>
export default {
    props: {
        title: String,
        buttonName: Boolean
    },
    computed:{
        homePage(){
            if(this.$route.path ==="/"){
                return true
            }
            return false
        } 
    }
}

</script>

<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>