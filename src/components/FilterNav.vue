<template>
    <nav class="filter-navbar">
        <button @click="filterBy('all')" :class="{active : current === 'all'}">
            All
        </button>
        <button @click="filterBy('complete')" :class="{active : current === 'complete'}">
            Complete
        </button>
        <button @click="filterBy('ongoing')" :class="{active : current === 'ongoing'}">
            OnGoing
        </button>

    </nav>
</template>

<script>
export default {
   props:['current'],
   methods:{
       filterBy(value){
           return this.$emit('filterMethod', value);
       }
   }
}
</script>

<style scoped>
    .filter-navbar{
       background-color: white;
    }

    .filter-navbar button{
        display: inline-block;
        color: gray;
        background-color: white;
    }

    .active{
        color: #000000;
        font-weight: bold;
    }
</style>