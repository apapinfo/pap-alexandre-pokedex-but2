<template>
  <div class="container">
    <PokemonSearch />
    <PokemonDetail v-if="afficher_details" :pokemon=mob @Fermer_image="fermetureDetails" />
    <PokemonList @Afficher_image="affichageDetails"/>
  </div>
</template>

<script>
import PokemonDetail from "../components/PokemonDetail.vue";
import PokemonList from "../components/PokemonList.vue";
import PokemonSearch from "../components/PokemonSearch.vue";

export default {
  components: {
    PokemonDetail,
    PokemonList,
    PokemonSearch,
  },

  data: function() { return {
    afficher_details : true,
  }},

  methods: {
    affichageDetails(){
      this.pokemon = "pokemon";
      this.afficher_details = true;
    },

    fermetureDetails(){
      this.afficher_details = false;
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 10px;
  width: calc(100% - 20px);
  min-height: calc(100vh - 20px);
  //background: radial-gradient(#ffbf0b, #e20000);

  font-family: "Acme", arial;
  font-size: 1rem;
  font-weight: normal;
}

h1 {
  color: #efefef;
}
</style>