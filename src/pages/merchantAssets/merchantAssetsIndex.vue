<template>
  <wraper>
    <aside>
      123
    </aside>
    <section>
      123
    </section>
  </wraper>
</template>

<script>
export default {};
</script>

<style lang="stylus" scoped>
px(a)
   a*(1440/1920) px
*
  margin 0
  padding 0

aside
  float left 
  border 1px solid black
  width px(280)
  height 100vh

section
  float right
  border 1px solid black
  width  px(1640)
  height 100vh
  
</style>
