<!--as-is-->

<template>
  <div>
    <input v-model="msg" />
    {{ msg }}
    <AsyncComponent :msg="testMsg" :obj="obj" />
  </div>
</template>

<script setup lang="ts">
import { ref, defineAsyncComponent } from "vue";
const msg = ref("test");

const testMsg = ref("testMsg");
const obj = { test: 1 };
const AsyncComponent = defineAsyncComponent({
  loader: () => {
    debugger;
    testMsg.value = "AsyncCompnent";
    obj.test = 2;
    return import("./AsyncComponent.vue");
  },
});
</script>

<!--to-be-->

<!-- <template>
  <div>
    <input v-model="msg" />
    {{ msg }}
    <AsyncComponent :msg="testMsg" />
  </div>
</template>

<script setup lang="ts">
import { ref, defineAsyncComponent } from "vue";
const msg = ref("test");

let testMsg = "testMsg";
const AsyncComponent = defineAsyncComponent({
  loader: () => {
    testMsg = "AsyncCompnent";
    return import("./AsyncComponent.vue");
  },
});
</script> -->
