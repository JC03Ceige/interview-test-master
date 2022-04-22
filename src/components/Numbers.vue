<template>
  <div>
    <div
      class="number"
      :id="'number-' + number"
      v-for="number in n()"
      :key="number"
      @mouseover="hov(number)"
      @mouseout="reset"
    >
      {{ number }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      limit: this.$parent.limit,
      numbers: []
    };
  },
  watch: {
    ["$parent.limit"](newLimit) {
      this.limit = newLimit;
    }
  },
  methods: {
    n() {
      let numbers = [];
      for (var i = 0; i < this.limit; i++) {
        numbers = [...numbers, i];
      }
      // The sort was changes from random to ascending. This will allow users to follow the numbers in a more natural way.
      return numbers.sort((a, b) => {
        return a - b;
      });
    },
    hov(number) {
      const nums = document.querySelectorAll(".number");

      for (let i = 0; i < nums.length; i++) {
        const num = nums[i].textContent.trim();
        if (number % num === 0) {
          nums[i].classList.add("active");
          console.log("divisor", num);
        }
      }
    },
    reset() {
      const nums = document.querySelectorAll(".number");
      nums.forEach(num => num.classList.remove("active"));
    }
  }
};
</script>

<style scoped>
/* Fonts are imported from Google Fonts because of the extensive library available. */
@import url("https://fonts.googleapis.com/css2?family=Abril+Fatface&family=Concert+One&family=Fredoka+One&display=swap");

/* The number components are styled to make it more readible to the user and easier to follow. */
.number {
  display: inline-block;
  padding: 0.25em;
  background-color: rgb(205, 246, 227);
  margin: 5px;
  font-family: "Concert One", cursive;
  font-size: 1.25em;
  width: 2em;
  height: 2em;
  border-radius: 4px;
  border: solid 0.5px darkslategray;
  box-shadow: inset -1px -1px 4px rgb(86, 100, 100),
    inset 2px 2px 4px rgb(215, 235, 235);
}

/* The color for the active number components where made softer so that it isn't as harsh on the user's eye
and more easily readible. */
.active {
  background-color: rgb(250, 108, 141);
}
</style>
