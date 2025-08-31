
<!-- src/components/ChipSwitch.vue -->
<template>
  <div class="chip-switch">
    <div
      class="chip"
      :class="{ selected: modelValue === 'higher' }"

    >
      Higher
    </div>
    <div
      class="chip"
      :class="{ selected: modelValue === 'lower' }"

    >
      Lower
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps<{ modelValue: string | null }>()

</script>

<style scoped>
.chip-switch {
  display: flex;
  gap: 12px;
  align-items: center;
}
.chip {
  padding: 8px 16px;
  border-radius: 24px;
  border: 1.5px solid black;

  user-select: none;
  font-weight: 600;
  transition: background-color 0.3s, color 0.3s;
  color: black;
  background-color: white;
}
.chip.selected {
  background-color: black;
  color: white;
  border-color: black;
}
.chip:hover {
  background-color: #333;
  color: white;
}
</style>
