<script setup lang="ts">
  defineProps<{
    labelText?: string;
    modelValue?: string;
    required?: boolean;
    error?: boolean;
    borderless?: boolean;
    placeholder?: string;
  }>();

  const emit = defineEmits(["update:modelValue"]);
</script>

<template>
  <BaseFormLabel :required="required" :label-text="labelText ? labelText : ''">
    <input
      @input="emit('update:modelValue', ($event.target as HTMLInputElement).value)"
      type="text"
      :value="modelValue"
      :class="`block outline-none border-gray-200 border-2 py-1 rounded-sm w-full hover:bg-gray-100 focus:border-blue-500 focus:border-solid focus:bg-transparent pl-1 ${
        error ? 'border-red-500 border-2' : ''
      } ${borderless ? 'border-transparent p-2' : ''}`"
      :placeholder="placeholder"
      v-bind="$attrs"
    />
  </BaseFormLabel>
</template>
