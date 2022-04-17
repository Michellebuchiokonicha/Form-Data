<script>
import {RouterLink, RouterView } from "vue-router";
// import InputData from "./components/InputData.vue";
// export default {
//   name: "App",
//   components: {InputForm}
// }
</script>

<template>
<!-- <div><InputData /></div> -->
<div class="enclose">
     
        <div class="former"><RouterLink to="/">FORM</RouterLink></div>
        <div class="dater"><RouterLink to="/data">DATA</RouterLink></div>
    
  
</div>
<RouterView />
</template>

<style>


#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.enclose {
  display: flex;
  justify-content: center;
  gap: 10px;
  color: aqua;
  text-decoration: none;
  font-size: 25px;
  font-weight: 700;
  font-family: Arial, Helvetica, sans-serif;
}

.former{
  text-decoration: none;
}
.dater{
  text-decoration: none;
}

body{
  margin: 0;
  background-color: #eee;
}

@media (hover: hover) {
 
}




@media (min-width: 1024px) {
 
  
}
</style>


