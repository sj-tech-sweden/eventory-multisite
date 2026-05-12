<template>
  <div v-if="showLabel" class="text-caption row items-center q-gutter-xs">
    <span>Done:</span>
    <q-icon :name="iconName" :color="iconColor" size="18px" />
  </div>
  <q-icon v-else :name="iconName" :color="iconColor" size="18px" />
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  item: {
    type: Object,
    default: () => ({}),
  },
  showLabel: {
    type: Boolean,
    default: false,
  },
})

const isDone = computed(() => Number(props.item?.out ?? 0) >= Number(props.item?.quantity ?? 0))
const iconName = computed(() => (isDone.value ? 'check_circle' : 'radio_button_unchecked'))
const iconColor = computed(() => (isDone.value ? 'positive' : 'grey-6'))
</script>
