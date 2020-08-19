<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header text-center">
            <strong>Order List</strong>
          </div>
          <div class="modal-body">
            <div v-if="foodCondition">
              <div
                v-for="food in orderedFood"
                :key="food.id"
                class="d-flex justify-content-between mb-2"
                style="border-bottom: 1px solid #f0f2f4;"
              >
                <img :src="'img/'+food.img" width="100" alt />
                <div>
                  <strong>{{food.name}}</strong>
                </div>
                <div>
                  <strong>{{food.quanity}}</strong>
                </div>
                <div>
                  <strong>{{Number(food.price.slice(0, -1))*(food.quanity)+"$"}}</strong>
                </div>
              </div>
            </div>
          </div>

          <div class="modal-footer">
            <slot>
              <button
                class="btn btn-danger modal-default-button btn-block"
                @click="$emit('close')"
              >ok</button>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: ["orderedFood", "count"],
  computed: {
    foodCondition: function() {
      return this.count > 0;
    }
  }
};
</script>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}
.modal-footer {
  border: none;
}
.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 80%;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  overflow: auto;
  height: 60%;
}

.modal-header h3 {
  margin-top: 0;
  color: #42b983;
}

.modal-body {
  /* margin: 20px 0; */
  padding: 0;
}

.modal-default-button {
  float: right;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>