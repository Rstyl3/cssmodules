<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p :class="$style.red">
      This takes normal class by name
    </p>
    <button :class="$style.btn">Other css</button>
    <button :class="$style.red">Second</button>
    <button :class="$style.bold">Third</button>
    <button :class="$style.blue">fourth</button>
    <button :class="$style.btnBig">fourth</button>
    <button :class="$style.otherfile">fourth</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style lang="postcss" module>
@import "../Css/something.css"; /*module can reach import classes*/

/*--red is a variable declared and located in Css/something.css*/
.red {
  color: var(--red);
}
.btnBig{
  padding: 5px;
  background-color: var(--black);
  color:white;
}
.blue{
  color:darkslateblue;
  padding: var(--big);
}
/*
Composes can fetch from other classes or from other files
Composes must be below the target class - compose is used by module
*/
.bold {
  composes: red;
  font-weight: bold;
}
/*Compose from other files*/
.otherfile{
  composes: nicebutton from "../Css/something.css"
}
</style>
