<template>
<!--  <button class="l-button">按钮</button>-->
  <button class="l-button" :class="{[`icon-${iconPosition}`]: true}" @click="$emit('click')">
    <l-icon class="icon" v-if="icon&& !loading" :name="icon"></l-icon>
    <l-icon class="loading icon" v-if="loading" name="loading"></l-icon>
    <div class="content">
      <slot></slot>
    </div>

</button>
</template>
<script>
  export default {
    props: {
      icon: {},
      loading:{
        type:Boolean,
        default: false
      },
      iconPosition: {
        type: String,
        default: 'left',
        validator (value) {
          return value === 'left' || value === 'right'
        }
      }
    }
  }
</script>
<style lang="scss">
@keyframes spin {
  0%{transform: rotate(0deg);}
  100%{transform: rotate(360deg);}


}
.l-button {
  font-size: var(--font-size);
  height: var(--button-height);
  padding: 0 1em;
  border-radius: var(--border-radius);
  border: 1px solid var(--border-color);
  background: var(--button-bg);
  display: inline-flex;
  justify-content: center;
  align-items: center;
  vertical-align: middle;
  &:hover {
    border-color: var(--border-color-hover);
  }
  &:active {
    background-color: var(--button-active-bg);
  }
  &:focus {
    outline: none;
  }
  &.icon-right {
    > .content { order: 1; }
    > .icon { order: 2; margin-right: 0; margin-left: .1em;}
  }
  .loading{
    animation: spin 1s infinite linear;
  }
}


</style>