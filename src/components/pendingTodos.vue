<template>
  <transition-group name="company">
    <template v-for="(item, index) in todos">
      <div :key="`key${index}`" v-if="!item.completed" class="margin-top">
        <el-checkbox
          @change="$emit('updateTheList', item, $event)"
          v-model="item.done"
        >
          <span :class="{ 'line-through': item.done }">{{
            item.text
          }}</span></el-checkbox
        >
      </div>
    </template>
  </transition-group>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      default: [],
    },
  },
};
</script>
