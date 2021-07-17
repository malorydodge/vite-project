<template>
  <h1>{{ msg }} {{ name }}</h1>
    <form class="form">
      <div class="form-horizontal-group">
        <input class="form-group__input" type="text" placeholder="Name" v-model="name"/>
        <button type="submit" class="button lg button-primary" 
        v-bind:disabled="name.length === 0" @click="submitForm">Submit</button>
      </div>
    </form>
    <li v-for="message in messages" :key="message.value">
      <SuccessMessage v-bind:msg="message" />
    </li>
  
</template>

<script lang="ts">
import { ref, defineComponent } from 'vue'
import SuccessMessage from './SuccessMessage.vue'
export default defineComponent({
  name: 'HelloWorld',
  components: {
    SuccessMessage
  },
  props: {
    msg: {
      type: String,
      required: true
    }
  },
  setup: () => {
    const name = ref('');
    let messages = ref(Array<string>());
    const submitForm = (e: Event) => {
      e.preventDefault();
      let formMsg = "Form submitted for: " + name.value;
      messages.value.push(formMsg);
    }
    return { name, messages, submitForm }
  }
})
</script>

<style scoped>
label {
  margin: 0 0.5em;
  font-weight: bold;
}

</style>
