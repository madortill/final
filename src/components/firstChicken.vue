<template>
  <div id="firstChicken">
    <div class="chicken1">
      <div class="nest1">
        
      </div>
    </div>
  </div>
</template>
 
<script>

export default {
  name: "first-chicken",
  components: {
    
  },
}
</script>

<style >
html,
body {
  margin: 0;
}

.chicken1 {
  background-image: url("../assets/media/chicken.png");
  width: 20vw;
  height: 20vh;
  background-size: 100% 100%;
  padding-right: 8vw;
  padding-left: 8vw;
}

.nest1 {
  background-image: url("../assets/media/chickenNest.png");
  width: 50vw;
  height: 30vh;
  background-size: 100% 100%;
  position: relative;
  top: 15%;
  right: 90%
}

</style>