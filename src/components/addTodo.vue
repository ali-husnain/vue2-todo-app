<template>
  <div class="input margin-top">
    <div class="flex">
      <el-input
        placeholder="Please input"
        size="small"
        class="border-none"
        v-model="inputValue"
      ></el-input>
      <el-button type="primary" size="small" @click="$emit('addTodo')" round
        >Add Item</el-button
      >
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: "",
    },
  },
  computed: {
    inputValue: {
      get() {
        return this.value;
      },
      set(val) {
        this.$emit("input", val);
      },
    },
  },
};
</script>
