<template>
  <nav class="bg-white border-b border-gray-200 fixed top-[88px] left-0 right-0 z-10 overflow-x-auto whitespace-nowrap scrollbar-hide">
    <div class="flex px-2">
      <button
        v-for="tab in tabs"
        :key="tab.id"
        @click="$emit('update:modelValue', tab.id)"
        class="px-4 py-3 text-sm font-medium transition-colors border-b-2"
        :class="modelValue === tab.id 
          ? 'text-green-600 border-green-600' 
          : 'text-gray-500 border-transparent hover:text-gray-700'"
      >
        {{ tab.label }}
      </button>
    </div>
  </nav>
</template>

<script setup>
defineProps({
  modelValue: String,
  tabs: Array
})
defineEmits(['update:modelValue'])
</script>

<style scoped>
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}
</style>