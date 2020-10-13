<template>
  <div class="row">
    <app-Quote
      v-for="(quote, index) in quotes"
      :key="quote"
      @click.native="deleteQuote(index)"
    >{{quote}}</app-Quote>
    <!-- Vue 2.2.0+的版本里，当在组件中使用v-for时，key是必须的 -->
  </div>
</template>

<script>
import Quote from "./Quote.vue";
export default {
  props: ["quotes"],

  components: {
    "app-Quote": Quote,
  },
  methods: {
    deleteQuote(index) {
      this.$emit("quoteDeleted", index);
    },
  },
};
</script>