<template>
  <span>{{ value }}</span>
</template>

<script>
export default {
  name: 'TextCell',
  props: {
    value: {
      type: [String, Number],
      default: ''
    }
  }
}
</script>