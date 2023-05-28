<script>
import { store } from '../store';
import AppCard from './AppCard.vue';

export default {
    
    
    data(){
        
        return{
            store,
        }
    },

    components: {
        AppCard,
    }
}
</script>


<template>
    <main>
        <div class="container">
            <div class="counter">Found {{ store.CharacterList.length }} Cards! This is your Deck! </div>
        <div class="container-cards">
            <AppCard v-for="Character in store.CharacterList" 
            :key="Character.id"
            :CharacterData="Character"
            />
        </div>
        </div>
        
    </main>
  
</template>

<style lang="scss" scoped>
@use '../assets/style/partials/variables' as *;
main{
    background-color: rgba(212,143,56,255);
}


.container{
    width: 80%;
    margin-inline: auto;
}

.counter{
    margin-inline: auto;
    background-color: rgba(33,37,41,255);
    color: white;
    height: 100px;
    padding: 1em;
    font-size: 2em;
    border-top-left-radius: 20px;
    border-top-right-radius: 20px;
}

.container-cards{
    border: 50px solid white;
    background-color: white;
    @include flex-margin-auto;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 1em;
    border-bottom-left-radius: 20px;
    border-bottom-right-radius: 20px;
}

</style>