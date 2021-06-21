<template>
  <slot name="test" :text = "'Slot test message'" :title="'Slot test title'"></slot>
</template>

<script>

export default {
  name: 'Child',
}
</script>
