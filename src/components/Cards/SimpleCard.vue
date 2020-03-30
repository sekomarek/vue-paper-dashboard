<template>
  <card>
    <div>
      <div class="row">
        <div class="col-12" v-if="$slots.header">
          <slot name="header"></slot>
        </div>
      </div>
      <div class="row">
        <div class="col-12" v-if="$slots.content">
          <slot name="content"></slot>
        </div>
      </div>
    </div>

  </card>
</template>
<script>
import Card from "./Card.vue";

export default {
  name: "simple-card",
  components: {
    Card
  }
};
</script>
<style>
</style>
