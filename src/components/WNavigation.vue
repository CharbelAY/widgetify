<template>
<div id="main-container" :style="mainContainerStyles">
  <slot></slot>
</div>
</template>

<script>

// import {convertToStyle} from "../helpers/conversionHelper";
export default {
name: "WNavigation",
  props:{
  wnavigationconf:Object
  },
  computed:{
  mainContainerStyles(){
    return (this.wnavigationconf["main-container"]);
  }
  }
}
</script>

<style scoped>

</style>
