<template>
  <label v-if="label">{{ label }}</label>
  <select
    :value="modelValue"
    v-bind="{
      ...$attrs,
      onChange: (event) => {
        emitToParent(event)
      }
    }"
  >
    <option
      v-for="option in options"
      :value="option"
      :key="option"
      :selected="option === modelValue"
    >
      {{ option }}
    </option>
  </select>
</template>

<script setup lang="ts">
import type { PropType } from 'vue'

const emits = defineEmits(['update:modelValue'])

defineProps({
  label: {
    type: String,
    default: ''
  },
  modelValue: {
    type: [String, Number],
    default: String
  },
  options: {
    type: Array as PropType<string[]>,
    required: true
  }
})

const emitToParent = (event: Event) => {
  const currentChange = (event.target as HTMLSelectElement).value
  emits('update:modelValue', currentChange)
}
</script>

<style scoped>
select {
  margin-block-end: 1rem;
}
</style>
