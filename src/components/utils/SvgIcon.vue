<template>
  <svg v-once aria-hidden="true" class="svg-icon-spin" :class="svgIcon">
    <use :xlink:href="symbolId" :fill="color" />
  </svg>
</template>

<script lang="ts" setup>
import { computed, reactive } from 'vue';

const props = defineProps({
  prefix: { type: String, default: 'icon' },
  name: { type: String, required: true },
  color: { type: String, default: '#ccc' },
  size: { type: String, default: 'default' },
});
const symbolId = computed(() => `#${props.prefix}-${props.name}`);
const svgIcon = computed(() => ({
  [`img-svg-size-${props.size}`]: props.size,
}));
const fontSize = reactive({ default: '32px', small: '20px', large: '48px' });
</script>
<style lang="scss" scoped>
.svg-icon-spin {
  width: v-bind('fontSize.default');
  height: v-bind('fontSize.default');
  color: v-bind(color);
  vertical-align: middle;
  fill: v-bind(color);

  &.img-svg-size-small {
    height: v-bind('fontSize.small');
    font-size: v-bind('fontSize.small');
  }

  &.img-svg-size-large {
    height: v-bind('fontSize.large');
    font-size: v-bind('fontSize.large');
  }
}
</style>
