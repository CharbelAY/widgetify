<template>
  <div id="main-container" data-readyForAnimation="true" :style="mainContainerStyles" @click="handleClick('main-container')">
    <slot></slot>
  </div>
</template>

<script>

// import {convertToStyle} from "../helpers/conversionHelper";
export default {
  name: "WNavigation",
  created() {
    this.registerAnimations(this.wnavigationconf['animations']);
  },
  methods: {
    animateWith(animation,onElement){
      let elementToAnimate = document.getElementById(onElement);
      if(elementToAnimate.getAttribute('data-readyForAnimation')==="true"){
        elementToAnimate.setAttribute('data-readyForAnimation',"false");
        elementToAnimate.className = animation;
        setTimeout(() => {
          elementToAnimate.classList.remove(animation);
          elementToAnimate.setAttribute('data-readyForAnimation',"true");
        }, 2000);
      }
    },
    /////////////////////
    registerAnimations(animations) {
      let style = document.createElement('style');
      style.type = 'text/css';
      for (const animation in animations) {
        let animationclass = "."+animation;
        animationclass+=`{animation-name: ${animation}; animation-duration: 2s; }`
        style.innerHTML = animations[animation]['keyframe']+` ${animationclass}`;
        document.getElementsByTagName('head')[0].appendChild(style); //todo check if maybe instead of head root div of component should be used
      }
    },
    handleClick(whichTag) {
      eval("this."+this.wnavigationconf[whichTag]["events"]["click"]["function"])(this.wnavigationconf[whichTag]["events"]["click"]["argument"],whichTag);
    }
  },
  props: {
    wnavigationconf: Object
  },
  computed: {
    mainContainerStyles() {
      return (this.wnavigationconf["main-container"]["styles"]);
    }
  }
}
</script>

<style scoped>

</style>
