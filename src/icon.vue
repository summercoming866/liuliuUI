<template>
  <svg class="l-icon">
    <use :xlink:href="`#icon-${name}`"></use>
  </svg>
</template>
<script>
export default {
  props: ['name']
}
</script>
<style lang="scss">
.l-icon {width: 1em; height: 1em; }
</style>