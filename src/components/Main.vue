<script setup>
import { ref, computed } from "vue";
import '../components/Main.css'

const todoTitle = ref("TODO");

const mode = ref(true);
const isDarkMode = ref(false);

function modeToggle() {
  mode.value = !mode.value;
  isDarkMode.value = !isDarkMode.value;
}

let id = 0;
const todos = ref([
  {
    id: id++,
    label: "10 party hats",
    completed: true,
    done: false,
  },
  {
    id: id++,
    label: "Jog around the park 3x",
    completed: false,
    done: false,
  },
  {
    id: id++,
    label: "Read for 1 hour",
    completed: false,
    done: false,
  },
  {
    id: id++,
    label: "Pick up groceries",
    completed: false,
    done: false,
  },
  {
    id: id++,
    label: "Complete Todo App on Frontend Mentor",
    completed: false,
    done: false,
  },
]);

const selectedFilter = ref("all");

const filteredTodos = computed(() => {
  if (selectedFilter.value === "all") {
    return todos.value;
  } else if (selectedFilter.value === "active") {
    return todos.value.filter((todo) => !todo.completed);
  } else if (selectedFilter.value === "completed") {
    return todos.value.filter((todo) => todo.completed);
  }
});

const newTodo = ref("");
const newAlreadyDone = ref(false);
const saveTodo = () => {
  todos.value.push({
    id: todos.value.length + 1,
    label: newTodo.value,
    completed: false,
    done: newAlreadyDone.value,
  });
  newTodo.value = "";
  newAlreadyDone.value = "";
};

function checkToggle(todo) {
  todo.completed = !todo.completed;
}
function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo);
}

function clearCompleted() {
  todos.value = todos.value.filter((todo) => !todo.completed);
}

const draggedItem = ref(null);
const draggedOverItem = ref(null);

function dragStart(index) {
  draggedItem.value = index;
}

function dragOver(index, event) {
  event.preventDefault();
  draggedOverItem.value = index;
}

function drop(index, event) {
  event.preventDefault();
  const draggedIndex = draggedItem.value;
  const draggedOverIndex = draggedOverItem.value;

  if (draggedIndex === draggedOverIndex) {
    return;
  }

  const temp = todos.value[draggedIndex];
  todos.value[draggedIndex] = todos.value[draggedOverIndex];
  todos.value[draggedOverIndex] = temp;

  draggedItem.value = null;
  draggedOverItem.value = null;
}
</script>

<template>
  <header :class="{ 'dark-mode': isDarkMode }">
    <nav>
      <a href="./home"
        ><h1>{{ todoTitle }}</h1></a
      >
      <div @click="modeToggle" class="image_container">
        <img v-if="mode" src="/icon-moon.svg" alt="DarkMode" />
        <img v-else src="/icon-sun.svg" alt="LightMode" />
      </div>
    </nav>
  </header>
  <section :class="{ 'dark-mode': isDarkMode }">
    <div class="container">
      <form class="add-todo-form" @submit.prevent="saveTodo">
        <div :class="{ 'dark-mode': isDarkMode }" id="container-input">
          <input type="checkbox" v-model="newAlreadyDone" />
          <input v-model="newTodo" placeholder="Create a new todo.." />
        </div>
      </form>
      <ul :class="{ 'dark-mode': isDarkMode }">
        <li
          v-for="(todo, index) in filteredTodos"
          :key="todo.id"
          :class="{
            completed: todo.completed,
            'dark-mode': isDarkMode,
          }"
          :draggable="true"
          @dragstart="dragStart(index)"
          @dragover="dragOver(index, $event)"
          @drop="drop(index, $event)"
        >
          <div
            @click="checkToggle(todo)"
            :class="{ 'check-mode': todo.completed }"
            class="image-container"
          >
            <img
              :class="{ 'dark-mode': isDarkMode }"
              src="/icon-check.svg"
              alt="icon-check"
            />
          </div>
          <p
            :class="{
              'dark-mode': isDarkMode,
              'check-mode': todo.completed,
              'already-done': todo.done,
            }"
          >
            {{ todo.label }}
          </p>
          <div @click="removeTodo(todo)" class="cross-container">
            <img src="/icon-cross.svg" alt="icon-check" />
          </div>
        </li>
        <li class="details" :class="{ 'dark-mode': isDarkMode }">
          <p>{{ todos.length }} items left</p>
          <button @click="clearCompleted">Clear Completed</button>
        </li>
      </ul>
      <p class="no-task" v-if="!todos.length">No task</p>
      <div class="filter" :class="{ 'dark-mode': isDarkMode }">
        <div class="filter-item">
          <button
            @click="selectedFilter = 'all'"
            :class="{ active: selectedFilter === 'all' }"
          >
            All
          </button>
          <button
            @click="selectedFilter = 'active'"
            :class="{ active: selectedFilter === 'active' }"
          >
            Active
          </button>
          <button
            @click="selectedFilter = 'completed'"
            :class="{ active: selectedFilter === 'completed' }"
          >
            Completed
          </button>
        </div>
      </div>
      <div class="drag">
        <p>Drag and drop to reorder list</p>
      </div>
    </div>
  </section>

  <footer>
    <div class="attribution">
      Challenge by
      <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
        >Frontend Mentor</a
      >. Coded by
      <a href="https://github.com/Fortunate-Codes" target="_blank"
        >Fortunate Adesina</a
      >.
    </div>
  </footer>
</template>
