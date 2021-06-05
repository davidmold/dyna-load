<template>
  <div class="view-detector">
    <div class="facade">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    window.addEventListener('scroll', this.onscroll, { passive:true})
  },
  methods: {
    onscroll() {
      let bb = this.$el.getBoundingClientRect()
      let btop = window.innerHeight
      if(bb.bottom >= 0 && bb.top <= btop){
        this.$emit('seen')
        window.removeEventListener('scroll', this.onscroll)
      }
    }
  }
}
</script>

<style>
.facade{
  height:600px;
  background-color:#ddd;
}
</style>