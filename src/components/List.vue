<template>
  <div class="list">
    <!-- new table -->
    <v-container>
      <v-simple-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-center">
                #
              </th>
              <th class="text-center">
                Date
              </th>
              <th class="text-center">
                Category
              </th>
              <th class="text-center">
                Count
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in list" :key="item.id" class="">
              <td>{{ item.id }}</td>
              <td>{{ item.data }}</td>
              <td>{{ item.category }}</td>
              <td>{{ item.count }} $</td>
              <span class="dot" @click="callContextMenu($event, item)">&#10247;</span>
              <ContextMenu></ContextMenu>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </v-container>
  </div>
</template>

<script>
import ContextMenu from './ContextMenu.vue';
export default {
  name: 'List',
  components: {
    ContextMenu,
  },
  mounted() {
    this.$context.EventEmitter.$on("show", this.show);
  },
  computed: {
    list() {
      return this.$store.getters.getPaymentsList
    },
  },
  methods: {
    callContextMenu(event, item) {
      this.$context.show(event.currentTarget, item);
    }
  },
};
</script>

<style lang="scss">
.list {
  width: 780px;
  margin: 0 auto;
  border-radius: 10px;
  background-color: #ddd;
  padding: 4px 0;
  box-sizing: border-box;

  &_title {
    list-style-type: none;
    display: flex;
    // justify-content: space-around;
    font-weight: bold;
    padding: 0;
  }



  &_item {
    display: flex;
    justify-content: space-around;
    padding: 10px 25px;
  }
}

.title-left {
  margin-left: 210px;
}

.title-cntr {
  margin-left: 130px;
}

.title-right {
  margin-left: 88px;
}

.context-menu {
  cursor: pointer;
  text-decoration: none;
}

.dot {
  cursor: pointer;
}
</style>