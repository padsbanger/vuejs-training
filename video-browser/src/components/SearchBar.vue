<template>
  <div class="search-input">
    <input @input="onInput"/>
  </div>
</template>


<script>
  export default {
    name: 'SearchBar',
    methods: {
      onInput(event) {
        this.$emit('termChange', event.target.value);
      }
    }
  };
</script>


<style scoped>
  .search-input {
    padding: 5px;
    display: flex;
  }
  .search-input input {
    padding: 5px;
    flex: 1;
  }
</style>