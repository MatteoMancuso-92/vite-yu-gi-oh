<script>
import {store} from '../store';

export default {
  data(){
    return{
      store,
    }
  },
  methods: {
        emitArchetypes() {
            this.$emit('performSearch');
        },
        resetArchetypes() {
            this.$emit('resetSearch');
        }
    },
}
</script>


<template>
  <nav>
    <div class="container">
      <div>
        <select v-model="store.searchArchetypes" @change="emitArchetypes">
      <option value="">Select an Archetype</option>
      <option v-for="archetype in store.ArrArchetypes" :key="archetype" :value="archetype.archetype_name">{{ archetype.archetype_name }}</option>
    </select>
    <button @click="resetArchetypes">Reset</button>
</div>
    </div>
  </nav>
</template>



<style lang="scss" scoped>
@use '../assets/style/partials/variables' as *;

nav{
    height: 100px;
    background-color: rgba(212,143,56,255);
    .container{
        height: 100%;
        width: 80%;
        @include flex-margin-auto;
        align-items: center;
    }

}

select{
    width: 200px;
    height: 50px;
    font-size: 1.1em;
    padding: .2em;
    border-radius: 10px;
    border: 2px solid black;
}

button{
  background-color: white;
    width: 100px;
    height: 50px;
    font-size: 1.1em;
    padding: .2em;
    border-radius: 10px;
    margin-left: 1em;
    border: 2px solid black;
}

</style>
