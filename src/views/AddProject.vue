<template>
  <h3>Add Project</h3>
  <form @submit.prevent="addProject">
      <label>Project Title</label>
      <br>
      <input type="text" v-model="title">
      <br>
      <label>Project Detail</label>
      <br>
      <input type="text" v-model="detail">
      <br>
      <button>Add Project</button>
  </form>
</template>

<script>
export default {
    data(){
        return {
            title : "",
            detail : "",
        }
    },
    methods:{
        addProject(){
           fetch('http://localhost:3000/projects', {
               method: "POST",
               headers:{
                   "Content-Type" : "application/json"
               },
              body:JSON.stringify({
                  title : this.title,
                  detail : this.detail,
                  complete : false,
              })
           })
           .then(()=>{
               return this.$router.push('/');
           })
           .catch((err)=>{
               console.log(err)
           })
        }
    }
}
</script>

<style>
    h3{
        margin-bottom: 30px;
    }
    form{
        height: 500px;
    }
    label{
        font-weight: bold;
        color: grey;
        margin-top: 20px;
    }
    input{
        width: 100%;
        border: none;
        border-bottom: 2px solid rgb(226, 217, 217);
        height: 60px;
        margin-bottom: 10px;
    }
    input:focus{
        outline: none;
    }

    button{
        margin: 10px auto;
        display: block;
        border: none;
        padding: 10px;
        color: white;
        border-radius: 10px;
        background-color: aquamarine;
    }
</style>