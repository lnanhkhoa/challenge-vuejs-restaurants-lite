<template>
  <div class="store-list">
    <p>Here you can find all of our restaurants. We have {{ storesCount }} stores right now!</p>
    <div class="store-list-wrapper">
      <Store class="store-list__item" :title="store.name" :photo="store.image" :location="store.location" v-for="store in storesWithImages" :key="store.id" />
    </div>
  </div>
</template>
<style lang="scss">
@import './StoreList.scss';
</style>
<script>
import Store from '@/components/Store/Store';
import map from 'lodash/map';
import size from 'lodash/size';

export default {
  name: 'StoreList',
  components: {
    Store
  },
  props: {
    stores: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    storesWithImages () {
      return map(this.stores, function (store) {
        store['image'] = 'https://via.placeholder.com/300?text=' + store.name;

        return store;
      });
    },
    storesCount () {
      return size(this.stores);
    }
  }
}
</script>
