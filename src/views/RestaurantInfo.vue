<template>
  <div class="page page__restaurant_info">
    <Banner
      :backgroundMedia="backgroundMedia"
      :text="text"
      textDistribution="bottom"
    />
  </div>
</template>

<script>
import Banner from "@/components/Banner/Banner"

export default {
  name: "Restaurant Info",
  components: {
    Banner,
  },
  data() {
    return {
      backgroundMedia: {
        type: "image",
        src: "https://via.placeholder.com/800x400?text=",
      },
    }
  },
  computed: {
    text(){
      return `Meals: ${this.$route.params.meals}`
    }
  },
  mounted() {},
}
</script>
