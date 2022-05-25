<template>
  <div class="todo-main">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span class="title-span">Checklist</span>
      </div>
      <div class="action-btn">
        <el-button
          @click="activeTab = 'pending'"
          round
          type="info"
          :class="{
            'button-animate':
              buttonAnimation && buttonToAnimation === 'pending',
          }"
          >Pending</el-button
        >
        <el-button
          @click="activeTab = 'completed'"
          round
          :class="{
            'button-animate':
              buttonAnimation && buttonToAnimation === 'completed',
          }"
          >Completed</el-button
        >
      </div>
      <div>
        <div v-if="activeTab === 'pending'" class="py-5">
          <PendingTodos :todos.sync="todos" @updateTheList="updateTheList" />
        </div>
        <div v-else class="py-5">
          <CompletedTodos :todos.sync="todos" @updateTheList="updateTheList" />
        </div>
        <AddTodo
          v-if="activeTab === 'pending'"
          v-model="input"
          @addTodo="addTodo"
        />
      </div>
    </el-card>
  </div>
</template>

<script>
import AddTodo from "./addTodo.vue";
import PendingTodos from "./pendingTodos.vue";
import CompletedTodos from "./completedTodos.vue";
export default {
  name: "TodoMain",
  components: {
    AddTodo,
    PendingTodos,
    CompletedTodos,
  },
  data() {
    return {
      buttonAnimation: false,
      activeTab: "pending",
      buttonToAnimation: "completed",
      input: "",
      todos: [
        {
          id: 1,
          text: "Learn JavaScript",
          done: false,
          completed: false,
        },
        {
          id: 2,
          text: "Learn Vue",
          done: false,
          completed: false,
        },
        {
          id: 3,
          text: "Build something awesome",
          done: false,
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.input) {
        this.todos.push({
          id: this.todos.length + 1,
          text: this.input,
          done: false,
          completed: false,
        });
        this.input = "";
      }
    },
    updateTheList(item, value) {
      if (item.completed) {
        this.buttonToAnimation = "pending";
      } else {
        this.buttonToAnimation = "completed";
      }
      setTimeout(() => {
        item.completed = !item.completed;
        this.buttonAnimation = true;
        setTimeout(() => {
          this.buttonAnimation = false;
        }, 100);
      }, 1000);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  buttontoanimationlist-style: none;
  padding-left: 10px;
}
.text {
  font-size: 14px;
}

.item {
  margin-bottom: 18px;
}
.border-none {
  border: none;
}
.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}
.clearfix:after {
  clear: both;
}

.box-card {
  width: 30%;
  margin: auto;
}

.action-btn {
  width: 100%;
  display: flex;
}
</style>
