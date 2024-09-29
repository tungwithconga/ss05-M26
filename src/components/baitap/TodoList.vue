<template>
  <div class="todo-app">
    <input v-model="newTask" placeholder="Enter your job" ref="taskInput" />
    <button @click="addTask">Add Job</button>

    <ul>
      <li v-for="(task, index) in tasks" :key="task.id">
        <input type="checkbox" v-model="task.status" @change="updateTaskStatus(task.id)" />
        <span :class="{ 'completed-task': task.status }">{{ task.name }}</span>
        <button @click="confirmDeleteTask(task.id)">Delete</button>
      </li>
    </ul>

    <div class="task-count">
      Số công việc hoàn thành: {{ completedTasksCount }} / {{ tasks.length }} công việc
    </div>

    <div v-if="showDeleteModal" class="modal">
      <p>Bạn có chắc muốn xóa công việc này?</p>
      <button @click="deleteTask">Xóa</button>
      <button @click="cancelDelete">Hủy</button>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, computed, onMounted } from 'vue';

const tasks = reactive([]);
const newTask = ref('');
const showDeleteModal = ref(false);
const taskToDelete = ref(null);

onMounted(() => {
  const storedTasks = JSON.parse(localStorage.getItem('tasks')) || [];
  tasks.push(...storedTasks);
});

const completedTasksCount = computed(() => tasks.filter(task => task.status).length);

const addTask = () => {
  if (newTask.value.trim() && !tasks.some(task => task.name === newTask.value)) {
    tasks.push({
      id: Date.now(),
      name: newTask.value,
      status: false,
    });
    newTask.value = '';
    updateLocalStorage();
  }
};

const updateTaskStatus = (taskId) => {
  const task = tasks.find(task => task.id === taskId);
  if (task) {
    task.status = !task.status;
    updateLocalStorage();
  }
};

const confirmDeleteTask = (taskId) => {
  taskToDelete.value = taskId;
  showDeleteModal.value = true;
};

const deleteTask = () => {
  const index = tasks.findIndex(task => task.id === taskToDelete.value);
  if (index !== -1) {
    tasks.splice(index, 1);
    updateLocalStorage();
  }
  showDeleteModal.value = false;
};

const cancelDelete = () => {
  showDeleteModal.value = false;
};

const updateLocalStorage = () => {
  localStorage.setItem('tasks', JSON.stringify(tasks));
};
</script>

<style scoped>
.todo-app {
  max-width: 400px;
  margin: 0 auto;
}

.completed-task {
  text-decoration: line-through;
}

.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 20px;
  border: 1px solid black;
  z-index: 1000;
}

.task-count {
  margin-top: 20px;
}
</style>
