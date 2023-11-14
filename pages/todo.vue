<template>
    <MainLayout>
        <div id="IndexPage" class="mt-4 max-w-[1200px] mx-auto px-2">
            <div>
                <h1>My To-Do List</h1>
                <input v-model="newTask" placeholder="Enter a new task" />
                <button @click="addTask">Add Task</button>
                <ul>
                <li v-for="(task, index) in tasks" :key="index">
                    {{ task }}
                    <button @click="deleteTask(index)">Delete</button>
                </li>
                </ul>
            </div>
        </div>
    </MainLayout>
</template>
<script setup>
    import MainLayout from "~/layouts/MainLayout.vue";

    const tasks = ref([]);
    const newTask = ref('');

    const addTask = () => {
      if (newTask.value !== '') {
        tasks.value.push(newTask.value);
        newTask.value = '';
      }
    };

    const deleteTask = (index) => {
      tasks.value.splice(index, 1);
    };
</script>

<style scoped>
h1 {
  text-align: center;
}

input {
  margin-bottom: 10px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 5px;
}

button {
  background-color: #f44336;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}
</style>