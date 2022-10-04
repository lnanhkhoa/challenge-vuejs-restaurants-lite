<template>
  <div class="recipe-form">
    <p>
      Introduce below the quantity for each ingredient you have and we will calculate how many Pasta
      Carbonara meals you can cook!
    </p>
    <form class="recipe-form__form">
      <label for="recipe-eggs">Eggs</label>
      <input
        v-model="eggs"
        class="recipe-form__form-input"
        type="number"
        name="eggs"
        id="recipe-eggs"
      />
      <label for="recipe-pasta">Pasta</label>
      <input
        v-model="pasta"
        class="recipe-form__form-input"
        type="number"
        name="pasta"
        id="recipe-pasta"
      />
      <label for="recipe-butter">Butter</label>
      <input
        v-model="butter"
        class="recipe-form__form-input"
        type="number"
        name="butter"
        id="recipe-butter"
      />
      <label for="recipe-milk">Milk</label>
      <input
        v-model="milk"
        class="recipe-form__form-input"
        type="number"
        name="milk"
        id="recipe-milk"
      />
      <label for="recipe-oil">Oil</label>
      <input
        v-model="oil"
        class="recipe-form__form-input"
        type="number"
        name="oil"
        id="recipe-oil"
      />
      <label for="recipe-bacon">Bacon</label>
      <input
        v-model="bacon"
        class="recipe-form__form-input"
        type="number"
        name="bacon"
        id="recipe-bacon"
        value="0"
      />
      <button type="submit" @click="calculate">Calculate</button>
    </form>
  </div>
</template>
<style lang="scss">
@import "./RecipeForm.scss";
</style>
<script>
import round from "lodash/round"
import min from "lodash/min"
export default {
  name: "RecipeForm",
  data() {
    return {
      eggs: 0,
      pasta: 0,
      oil: 0,
      butter: 0,
      milk: 0,
      bacon: 0,
      meals: 0,
    }
  },
  props: {
    ingredients: {
      type: Object,
      default: () => ({}),
    },
  },
  methods: {
    calculate(event) {
      event.preventDefault()
      this.meals = min([
        round(this.eggs / this.ingredients.eggs),
        round(this.pasta / this.ingredients.pasta),
        round(this.oil / this.ingredients.oil),
        round(this.butter / this.ingredients.butter),
        round(this.milk / this.ingredients.milk),
        round(this.bacon / this.ingredients.bacon),
      ])
      this.$router.push({
        name: "Restaurant Info",
        params: { meals: this.meals },
      })
    },
  },
}
</script>
