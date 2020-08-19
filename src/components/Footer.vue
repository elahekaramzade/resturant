<template>
  <footer class="footer">
    <div class="circle" @click="openModal">
      <div class>
        <div class="item-footer">
          <span class="icon-basket"></span>
          <transition
            enter-active-class="animate__animated animate__bounce"
            leave-active-class="animated fadeOut"
            mode="out-in"
          >
            <div class="counter" :key="count">{{count}}</div>
          </transition>
        </div>
      </div>
    </div>
    <modal v-if="showModal" @close="showModal = false" :orderedFood="orderedFood" :count="count"></modal>
  </footer>
</template>

<script>
import Modal from "./Modal";
export default {
  components: { Modal },
  props: ["orderedFood"],
  data() {
    return {
      count: 0,
      showModal: false
    };
  },
  methods: {
    openModal() {
      this.showModal = true;
    },
    orderCount: function() {
      let quanity = this.orderedFood.map(m => {
        return m.quanity;
      });
      this.count = quanity.reduce(function(a, b) {
        return a + b;
      }, 0);
    }
  },
  watch: {
    orderedFood: {
      handler: function(newValue) {
        if (newValue) this.orderCount();
      },
      deep: true
    }
  },
  beforeMount: function() {
    this.orderCount();
  }
};
</script>

<style>
/* Sticky footer styles
-------------------------------------------------- */

body {
  overflow-x: hidden;
}
.footer {
  position: fixed;
  bottom: 5px;
  /* width: 100%; */
  height: 60px; /* Set the fixed height of the footer here */
  line-height: 60px; /* Vertically center the text there */
  right: 5px;
}

/* Custom page CSS
-------------------------------------------------- */
/* Not required for template or sticky footer method. */

.circle {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background-color: #f5f5f5;
}
.item-footer {
  font-size: 2rem;
  text-align: center;
}
.counter {
  position: absolute;
  right: 34px;
  text-align: center;
  top: -10px;
  line-height: 15px;
  font-size: 17px;
  background: #e13548;
  height: 30px;
  width: 30px;
  border-radius: 50px;
  padding-top: 6px;
}
</style>