<script>
import BaseHeader from './components/BaseHeader.vue';
import BaseMain from './components/BaseMain.vue';
import BaseFooter from './components/BaseFooter.vue';

import { store } from './data/store';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    BaseHeader,
    BaseMain,
    BaseFooter,
  },
  data() {
    return {
      store,
    }
  },
  mounted() {
    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0").then(result => {
      console.log("risultato:", result.data.data);
      this.store.carte = result.data.data;
      this.store.loading = false;
    });

    console.log("Store:",this.store)
  }
}
</script>

<template>

  <BaseHeader/>
  <BaseMain/>
  <BaseFooter/>

</template>

<style scoped>

</style>
