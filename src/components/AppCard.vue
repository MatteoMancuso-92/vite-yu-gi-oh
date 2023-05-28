<script>

export default {
    props: {
        CharacterData: Object,
    }

}
</script>


<template>
  <div class="card">
    <img :src="CharacterData.card_images[0].image_url" :alt="CharacterData.name">
    <h3>{{ CharacterData.name }}</h3>
    <div class="species">{{ CharacterData.race }} </div>
  </div>
</template>



<style lang="scss" scoped>
@use '../assets/style/partials/variables' as *;
.card{
    width: 200px;
    height: 400px;
    text-align: center;
    background-color: $brand-color;
    border-bottom-left-radius: 20px;
    border-bottom-right-radius: 20px;

    img{
        width: 100%;
    }

    h3{
        margin-top: 1em;
        color: white;
    }

    .species{
        margin-top: 1em;
    }


}

</style>