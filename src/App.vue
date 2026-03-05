<template>
  <div class="container">
    <h1>🚀 Vue DevOps Exam Project</h1>

    <div class="card">
      <input
        v-model="newTask"
        placeholder="Nhập công việc..."
        @keyup.enter="addTask"
      />
      <button @click="addTask">Thêm</button>
    </div>

    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button class="delete" @click="removeTask(index)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.tasks.push(this.newTask);
        this.newTask = "";
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f4f6f9;
}

.container {
  max-width: 600px;
  margin: 50px auto;
  text-align: center;
}

h1 {
  color: #42b983;
}

.card {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 10px;
  font-size: 16px;
}

button {
  padding: 10px 15px;
  cursor: pointer;
  background: #42b983;
  color: white;
  border: none;
}

button:hover {
  opacity: 0.8;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  background: white;
  padding: 10px;
  margin-bottom: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.delete {
  background: red;
}
</style>