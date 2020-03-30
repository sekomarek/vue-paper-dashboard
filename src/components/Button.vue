<template>
  <component
    :is="tag"
    :type="nativeType"
    :disabled="disabled || loading"
    class="btn"
    :class="[
      {'btn-round': round},
      {'btn-block': block},
      {'btn-with-icon': withIcon},
      {'btn-just-icon': icon},
      {[`btn-color-${color}`]: type},
      {[`btn-${type}`]: type && !outline},
      {[`btn-outline-${type}`]: type && outline},
      {[`btn-${size}`]: size},
      {'btn-link': simple}
    ]">
    <slot name="loading">
      <i v-if="loading" class="fa fa-spinner fa-spin"></i>
    </slot>
    <slot></slot>
    <slot name="with-icon">
      <i v-if="withIcon" :class="iconClass"></i>
    </slot>
  </component>
</template>
<script>
export default {
  name: 'p-button',
  props: {
    tag: {
      type: String,
      default: "button"
    },
    round: Boolean,
    icon: Boolean,
    withIcon: Boolean,

    outline: Boolean,
    block: Boolean,
    loading: Boolean,
    disabled: Boolean,
    type: {
      type: String,
      default: "default"
    },
    nativeType: {
      type: String,
      default: "button"
    },
    size: {
      type: String,
      default: ""
    },
    iconClass: {
      type: String,
      default: "ti-hand-point-up"
    },
    color: {
      type: String,
      default: ""
    },
    simple: Boolean
  }
};
</script>
<style>
</style>
