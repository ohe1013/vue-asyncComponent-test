<template>
  <div>
    {{ msg }}
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{ msg: string; obj: Object }>();
console.log(props.msg);
console.log(props.obj);
</script>
