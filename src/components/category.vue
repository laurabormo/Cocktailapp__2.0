<template>
  <div>
    <md-list>
      <div v-for="drink in drinks" :key="drink.idDrink">
        <md-list-item :to="'/drink/' + drink.idDrink">
          <md-avatar class="md-large">
            <img :src="drink.strDrinkThumb" />
          </md-avatar>
          <span class="md-list-item-text">{{ drink.strDrink }}</span>
        </md-list-item>
        <md-divider> </md-divider>
      </div>
    </md-list>
  </div>
</template>

<script>
import DataService from "../dataservice";
export default {
  name: "category",
  data() {
    return {
      drinks: [],
    };
  },
  created: function () {
    DataService.getCockbyCateg(this.$route.params.category).then((data) => {
      this.drinks = data.data.drinks;
    });
  },
};
</script>

<style >
</style>
