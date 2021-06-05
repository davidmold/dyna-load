<template>
  <div class="hello">
    <div class="above-fold">
      <div>This is all above the fold</div>
    </div>
    <view-detector v-on:seen="sawitem = true">
      <complex-component v-if="sawitem"></complex-component>
    </view-detector>
  </div>
</template>

<script>
import ViewDetector from './ViewDetector.vue'
import { defineAsyncComponent } from 'vue'
export default {
  components: {
    ViewDetector,
    ComplexComponent: defineAsyncComponent(() => {
      console.log('loading complex component now')
      return import('./ComplexComponent.vue')
    })
  },
  data() {
    return {
      sawitem: false
    }
  }
}
</script>
<style>
.above-fold{
  min-height:100vh;
  display:flex;
  flex-direction: column;
  justify-content: center;
  background-color:#eee;
}

.above-fold div{
  text-align: center;
}
</style>
