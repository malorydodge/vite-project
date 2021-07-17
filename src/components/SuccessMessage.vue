<template>
  {{msg}} <i class="fa fa-check"></i>  
</template>

<script lang="ts">
import { ref, defineComponent } from 'vue'
export default defineComponent({
  name: 'SuccessMessage',
  props: {
    msg: {
      type: String,
      required: true
    }
  },
  setup: () => {
    const text = ref('');
    return { text }
  }
})
</script>

<style scoped>

</style>
