<template>
  <div id="app">
    <!-- An h1 one element is inserted to tell the user how they can use the app. -->
    <h1>
      This web app allows you to see the dividers of any number that you hover
      your mouse over.
      <br />
      To get started, please enter a number below to choose how many numbers
      should be displayed on the grid.
    </h1>
    <input type="number" v-model="limit" />
    <!-- A container div is inserted for the Numbers component. This is done to make it more managable. -->
    <div class="num-grid">
      <Numbers />
    </div>
  </div>
</template>

<script>
import Numbers from "@/components/Numbers";

export default {
  name: "App",
  /* The background color is changes with this block of code. Because of the nature of app, it is easier for the user to concentrate
  when the background color is darker. */
  beforeCreate() {
    document.querySelector("body").setAttribute("style", "background:#002255");
  },
  beforeDestroy() {
    document.querySelector("body").setAttribute("style", "");
  },
  components: { Numbers },
  data() {
    return {
      limit: 100
    };
  }
};
</script>

<style scoped>
/* Google Fonst are use because of their extensive font library. */
@import url("https://fonts.googleapis.com/css2?family=Abril+Fatface&family=Concert+One&family=Cuprum&family=Fredoka+One&display=swap");

/* As a default, all margins and padding is reset to 0. This helps with styling individual components. */
* {
  margin: 0;
  padding: 0;
}

/* The font for the entire app is changes and we implement a 1em margin. */
#app {
  margin: 1em !important;
  font-family: "Cuprum", sans-serif !important;
}

/* For all of the following components, absolute positioning is used, because it is a dynamically loaded grid, it could cause
problems with elements jumping around. Absolute positioning helps prevent this. */

/* The h1 is styled to make it appear as a banner accross the screen. It just looks slightly more professional. */
h1 {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(230, 230, 250, 0.79);
  width: 110%;
  font-size: 1.5rem;
  letter-spacing: 2px;
  height: 10%;

  /* position the div in center */
  position: absolute;
  top: 5%;
  left: -5%;
}

/* The input is style to be more attractive and the rounded corners just make look more refined and elegant. */
input {
  margin: 10px;
  padding: 0.7em;
  display: flex;
  justify-content: center;
  align-items: center;

  /* position the div in center */
  position: absolute;
  top: 20%;
  left: 12%;

  border-radius: 15px;
  border: solid 0.5px rgb(255, 233, 133) !important;
  box-shadow: inset 2px 2px 4px rgb(220, 220, 145),
    inset 3px 4px 6px rgb(223, 223, 174), inset 5px 7px 9px lightgoldenrodyellow,
    inset -2px -2px 2px rgb(215, 235, 235);
  font-size: 1.2rem;
  height: 0.5em;
}

/* This is done for accesibility and allows the user to see it is active. */
input[type="number"]::-webkit-inner-spin-button {
  cursor: pointer;
}

/* The number grid div is styled seperately to allow for absolute positioning. */
.num-grid {
  padding: 5px;
  display: inline-flex;
  justify-content: center;
  align-items: center;

  /* position the div in center */
  position: absolute;
  top: 40%;
  left: 20%;
  transform: translate(-10%, -10%);
}
</style>
