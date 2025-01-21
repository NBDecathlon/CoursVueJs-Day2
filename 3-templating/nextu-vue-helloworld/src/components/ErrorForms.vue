<template>
  <span class="error">{{ message }}</span>
</template>

<script>
export default {
  name: 'ErrorForms',
  props: {
    message: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.error {
  color: #e74c3c;
  font-size: 14px;
  font-weight: 500;
  background-color: #f8d7da;
  padding: 8px 12px;
  border-radius: 5px;
  display: inline-block;
  margin-top: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.error:hover {
  background-color: #f5c6cb;
}
</style>
