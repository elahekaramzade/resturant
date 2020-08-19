<template>
  <div class="mt-4">
    <div class="d-flex justify-content-center">
      <div class v-for="item in categories" :key="item.name">
        <div
          class="cat-box"
          @click="setFilter(item.name)"
          :class="{ active: currentFilter === item.name }"
        >
          <span :class="'icon-'+item.icon"></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentFilter: "",
      categories: [
        { icon: "pizza", name: "pizza" },
        { icon: "food", name: "burger" },
        { icon: "chicken", name: "chicken" },
        { icon: "plate", name: "dish" }
      ]
    };
  },
  methods: {
    setFilter: function(filter) {
      this.currentFilter = filter;
      this.$emit("passcurrentFilter", this.currentFilter);
    }
  }
};
</script>

<style>
.cat-box {
  border: 1px solid;
  font-size: 3rem;
  border-radius: 10px;
  background: #fcab71;
  color: white;
  height: 80px;
  width: 80px;
  text-align: center;
}
.cat-box.active {
  background: #e13548;
}
</style>