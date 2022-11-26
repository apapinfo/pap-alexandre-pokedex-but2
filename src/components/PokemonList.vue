<template>
  <div class="list">
    <article v-for="mob in pokemons" :key="mob.name" v-on:click="afficher_details(mob)">
      <img :src="url_image + mob.name + '.png'" alt="Erreur : Image non chargée">
      <h3> 
        {{mob.name}} 
      </h3>
    </article>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  nom: "PokemonList",
  data: function() { return {
    pokemons : {},
    url_image : "https://img.pokemondb.net/sprites/bank/normal/",
  };
  },

  created(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=-1").then(response => (this.pokemons = response.data.results));
  },

  methods: {
    afficher_details(mob){
      this.$emit("Afficher_image", mob);
    }
  }
};
</script>

<style lang="scss" scoped>
.list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  grid-gap: 10px;
  width: 100%;
  max-width: 510px;
}
article {
  height: 150px;
  background-color: #efefef;
  text-align: center;
  text-transform: capitalize;
  border-radius: 5px;
  cursor: pointer;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}
h3 {
  margin: 0;
}
#scroll-trigger {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 150px;
  font-size: 2rem;
  color: #efefef;
}

img {
  width: 96px;
  height: 96px;
}
</style>

