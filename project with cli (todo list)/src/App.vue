<script setup>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <div class="container">
    <Header @toggle-add-task='toggleAddTask' title="Task Tracker" :buttonName="showAddTask"/>
     <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script>
export default {
  data(){
    return{
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
  },
}
</script>



