<script>
import {store} from './store';

import AppFilter from './components/AppFilter.vue';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';
import AppLoader from './components/AppLoader.vue';



export default {

  data(){
    
    return {
      store,
    }

  },

  
  
  components: {
    AppHeader,
    AppFilter,
    AppMain,
    AppLoader,
  },

  methods: {
    filteredArchetypes() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php', {
        params: {
          num:20,
          offset:0,
          archetype: this.store.searchArchetypes,
        }
      })
      .then(response => (this.store.CharacterList = response.data.data));
    },
    reset() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
      .then(response => (this.store.CharacterList = response.data.data));
      this.store.searchArchetypes = ''
    }, 
  },
  created() {
    axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
    .then(response => (this.store.CharacterList = response.data.data));
     
    axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')   
    .then(response => (this.store.ArrArchetypes = response.data));
    
  },

}
</script>

<template>
  <AppHeader/>
  <AppFilter @performSearch="filteredArchetypes" @resetSearch="reset"/>
  <AppLoader v-show="store.CharacterList.length === 0"/>
  <AppMain/> 
</template>

<style lang="scss">

@use './assets/style/general.scss'


</style>