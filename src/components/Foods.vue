<template>
  <div class="container">
    <div class="row" v-for="food in filterFood" :key="food.index">
      <div class="col-sm-12">
        <div class="food-box d-flex">
          <div class="img-handler">
            <img :src="'img/'+food.img" alt width="150" />
          </div>
          <div class="detail">
            <p>
              <strong>{{food.name}}</strong>
            </p>
            <p>
              <strong class="text-danger">{{food.price}}</strong>
            </p>
          </div>
          <div class="add-btn">
            <button class="btn btn-xs btn-danger add" @click="addFood(food)">+</button>
            <span style="margin: 0 5px;">{{food.quanity}}</span>
            <button
              class="btn btn-xs btn-danger add"
              style="padding-right: 5px;
                     padding-left: 5px;"
              @click="removeFood(food)"
            >-</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["currentFilter"],
  data() {
    return {
      orderedFood: [],
      foods: [
        {
          img: "pizza1.jpg",
          name: "Peperoni",
          price: "15$",
          tag: "pizza",
          id: 1,
          quanity: 0
        },
        {
          img: "pizza2.jpg",
          name: "Margarita",
          price: "15$",
          tag: "pizza",
          id: 2,
          quanity: 0
        },
        {
          img: "dish1.jpg",
          name: "Mix Dish",
          price: "15$",
          tag: "dish",
          id: 3,
          quanity: 0
        },
        {
          img: "dish2.jpg",
          name: "Special Dish",
          price: "15$",
          tag: "dish",
          id: 4,
          quanity: 0
        },
        {
          img: "burger1.jpg",
          name: "Classic Burger",
          price: "15$",
          tag: "burger",
          id: 5,
          quanity: 0
        },
        {
          img: "burger2.jpg",
          name: "chicken Burger",
          price: "15$",
          tag: "burger",
          id: 6,
          quanity: 0
        },
        {
          img: "chicken1.jpg",
          name: "Chicken Spicy",
          price: "15$",
          tag: "chicken",
          id: 7,
          quanity: 0
        },
        {
          img: "chicken2.jpg",
          name: "Chicken",
          price: "15$",
          tag: "chicken",
          id: 8,
          quanity: 0
        }
      ]
    };
  },
  computed: {
    filterFood() {
      if (this.currentFilter) {
        return this.foods.filter(f => {
          return f.tag === this.currentFilter;
        });
      }
      return this.foods;
    }
  },
  methods: {
    addFood: function(food) {
      if (food.quanity == 0) {
        food.quanity++;
        this.orderedFood.push(food);
      } else {
        food.quanity++;
        let detectedFood = this.orderedFood.find(f => {
          return f.id == food.id;
        });
        detectedFood.quanity = food.quanity;
      }
      this.$emit("passCount", this.orderedFood);
    },
    removeFood: function(food) {
      if (food.quanity > 0) {
        food.quanity--;
        let detectedFood = this.orderedFood.find(f => {
          return f.id == food.id;
        });
        detectedFood.quanity = food.quanity;
      } else if (food.quanity == 0) {
        this.orderedFood.splice(food);
      }
      this.$emit("passCount", this.orderedFood);
    }
  }
};
</script>

<style>
.food-box {
  border: 1px solid gainsboro;
  border-radius: 5px;
  margin: 15px 0;
  /* padding: 10px; */
}
.add-btn {
  position: absolute;
  bottom: 25px;
  right: 25px;
}
.add {
  font-size: 20px;
  line-height: 10px;
  padding-top: 2px;
  padding-right: 3px;
  padding-left: 3px;
  transition: 1ms ease all;
}
.img-handler {
  margin-right: 10px;
}
button.btn.btn-xs.btn-danger.add:active {
  transform: scale(1.4);
}
</style>