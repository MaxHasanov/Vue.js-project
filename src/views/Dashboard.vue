<template>
  <div class="home">
    <v-btn color="gray" large class="add-new-item" @click="clicked">ADD NEW COST +</v-btn>
    <Popup v-if="isPopupActive"></Popup>
    <List></List>
    <div class="pagination">
      <v-btn v-on:click="$store.commit('prevPage')">prev</v-btn>
      <v-btn v-on:click="$store.commit('nextPage')">next</v-btn>
    </div>
  </div>
</template>

<script>
import List from '@/components/List.vue'
import Popup from '@/components/popup.vue'

export default {
  name: 'Dashboard',
  components: { List, Popup, },
  data() {
    return {
      isPopupActive: false,
    }
  },
  methods: {
    clicked() {
      this.isPopupActive = !this.isPopupActive;
    }
  }
}
</script>

<style lang="scss">
.add-new-item {
  margin: 20px 0;
  padding: 3px;
  width: 200px;
  border-radius: 7px;
  height: 35px;
}

.add-new-item:hover {
  border-color: red;
}

.pagination {
  margin: 15px 0;
}

.pagination button {
  width: 70px;
  height: 25px;
  border-radius: 5px;
  margin: 0 15px 0 0;
}

.pagination button:hover {
  border-color: red;
}
</style>