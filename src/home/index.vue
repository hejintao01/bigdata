<template>
  <div>
    <stock></stock>
    <dull></dull>
  </div>
</template>
<script>
import stock from '../components/stock.vue'
import dull from '../components/dull.vue'
export default {
  name: 'home',
  data() {
    return {
    }
  },
  components: {
    stock,
    dull
  },

}
</script>
<style>
/* .parentbox {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  height: 100%;
  justify-content: space-between;
  background: linear-gradient(#31589e, #3c69ba);
}
.parentbox:after {
  content: "";
  flex: auto;
} */
</style>
