<template>
  <nav>
      <router-link to="/">Projects</router-link>
       <router-link :to="{name : 'addProject'}">Add Project</router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style scoped>
    nav{
        text-align: center;
        margin-top: 20px;
    }

    nav a{
        text-decoration: none;
        margin: 10px;
        color: gray;
        font-weight: bold;
    }

    .router-link-active{
        border-bottom: 3px solid aquamarine;
        padding-bottom: 10px;
    }
  
</style>