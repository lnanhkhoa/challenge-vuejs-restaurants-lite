<template>
  <div class="page page__stores">
    <p>{{ welcomeMessage }}</p>
    <div class="pages__stores-list">
      <label>Search: </label>
      <input type="text" name="textSearch" v-model="textSearch" v-value="textSearch" @input="onSearch" />
      <StoreList :stores="stores" />
    </div>
  </div>
</template>

<script>
import moment from "moment"
import StoreList from "@/components/StoreList/StoreList"
const stores = require("@/assets/stores/stores.json")

export default {
  name: "Stores",
  components: {
    StoreList,
  },
  data() {
    return {
      currentTime: moment().format("dddd, MMMM Do YYYY, h:mm:ss a"),
      stores,
      textSearch: "",
    }
  },
  computed: {
    welcomeMessage() {
      return "Welcome to our restaurants list! Your local time is: " + this.currentTime
    },
  },
  methods: {
    onSearch(e) {
      const searchStr = e.target.value;
      this.stores = stores.filter((i) => {
        const isMatched = i.name?.indexOf(searchStr) !== -1
        return isMatched
      })
    },
  },

  mounted() {
    const setTimer = () =>
      setTimeout(() => {
        this.currentTime = moment().format("dddd, MMMM Do YYYY, h:mm:ss a")
        setTimer()
      }, 1000)
    setTimer()
  },
}
</script>
