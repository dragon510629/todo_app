<template>
  <div>{{ remaining }} items left</div>
</template>

<script>
export default {
  name: 'todo-remaining',
  created() {
    eventBus.$on('pluralize', this.handlePluralize)
  },
  beforeDestroy() {
    eventBus.$off('pluralize', this.handlePluralize)
  },
  methods: {
    handlePluralize() {
      console.log(1233);
      this.$store.dispatch('addTodo', {
        'id': this.todosFiltered.length + 1,
        'title': "haha",
      })
    }
  },
  computed: {
    remaining() {
      return this.$store.getters.remaining
    },
    todosFiltered() {
      return this.$store.getters.todosFiltered
    }
  }
}
</script>

