<template>
      <div class="div" :class="{complete :project.complete}">
        <div class="container">
             <div>
                <h3 @click="showDetail = !showDetail">{{project.title}}</h3>
              </div>
                <div>
                    <span class="material-icons" @click="deleteItem">
                        delete
                    </span>
                  
                    <router-link :to="{name : 'editProject', params:{id : project.id}}">
                        <span class="material-icons">
                            mode_edit
                        </span>
                    </router-link>
                    <span class="material-icons" @click="completeProject">
                        done
                    </span>
                </div>
        </div>
          <p v-if="showDetail">{{project.detail}}</p>
      </div>
</template>

<script>
export default {
    props:['project'],
    data(){
        return {
            showDetail : false,
            api : "http://localhost:3000/projects/",
        }
    },
    methods:{
       deleteItem(){
           let deleteRoute = this.api+this.project.id;
           fetch(deleteRoute, {method:"DELETE"})
           .then(()=>{
               this.$emit("delete", this.project.id)
           })
           .catch((error)=>{
               console.log(error.message());
           })
       },
       completeProject(){
           let updateProject = this.api + this.project.id;
           fetch(updateProject, {
               method : "PATCH",
               headers : {
                   "Content-Type" : "application/json"
               },
               body :JSON.stringify({
                   complete : !this.project.complete
               })
           })
           .then(()=>{
               return this.$emit("complete", this.project.id)
           })
           .catch((error) => {
               console.log(error.message)
           })
       }
    }
}
</script>

<style scoped>
    .div{
        background-color:white;
        padding: 10px;
        margin: 10px 0;
        box-shadow: 0 3px 2px rgb(138, 135, 135);
        border-left: 8px solid crimson;
        border-radius: 10px;
    }

    h3{
        color: rgb(0, 68, 255);    
        cursor: pointer;
    }
    .container{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    span{
        margin-left: 12px;
        cursor: pointer;
    }
    .complete{
        border-left-color: lime;
    }
</style>>

