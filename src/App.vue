<template>
  <div id="app">
    <TodoMain />
  </div>
</template>

<script>
import TodoMain from "./components/TodoMain";

export default {
  name: "App",
  components: {
    TodoMain,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.flex {
  display: flex;
  align-items: center;
}
.py-5 {
  padding-top: 15px;
  padding-bottom: 15px;
}
.margin-top {
  margin-top: 10px;
  margin-bottom: 10px;
}
.line-through {
  text-decoration: line-through;
}
.company-enter-active,
.company-leave-active {
  transition: all 0.2s;
}
.company-enter {
  opacity: 0;
  transform: translateY(100%);
}

.company-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
.company-enter-active {
  transition-delay: 0.2s;
}

.company2-enter-active,
.company2-leave-active {
  transition: all 0.2s;
}
.company2-enter {
  opacity: 0;
  transform: translateY(100%);
}

.company2-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}
.company2-enter-active {
  transition-delay: 0.2s;
}
.button-animate {
  transform: scale(1.1);
}
</style>
