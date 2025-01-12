
<template>
  <div>
    <input 
    type="text"
    placeholder="Recherche..."
    @input="onInputChange"
    />
  </div>
</template>

<script>
export default {
  methods: {
    onInputChange(event) {
      this.$emit("search", event.target.value);
    },
  },
  };
</script> 