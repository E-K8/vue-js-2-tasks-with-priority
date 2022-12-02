<template>
  <v-container>
    <section class="panel">
      <input type="checkbox" />

      <select v-model="selectedPriority" class="priority">
        <option v-for="prio in priorities" :key="prio">
          {{ prio.label }}
        </option>
      </select>
      <input
        type="text"
        v-model="newTask"
        @keyup.enter="addTask"
        placeholder="Enter a new task"
        class="text-input"
      />
      <button class="btn" @click="clearList">
        {{ areAnySelected ? 'Delete Selected' : 'Clear List' }}
      </button>
    </section>

    <section class="list">
      <ul v-if="tasks.length > 0">
        <li
          v-for="task in tasks"
          :key="{ done: task.checked, low: task.priority.prio === 0 }"
        >
          <input type="checkbox" v-model="task.checked" />
          <label for="checkbox">
            [{{ task.priority.label }}] {{ task.text }}
          </label>
          <button @click="removeTask(task)">X</button>
        </li>
      </ul>
      <!-- <template v-else>
        <p class="center-text">All done!</p>
      </template> -->
    </section>
  </v-container>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      newTask: '',
      tasks: [
        {
          text: 'Sample task',
          priority: { label: 'Priority 1', prio: 1 },
          checked: false,
        },
      ],
      priorities: [
        { prio: 0, label: 'Select Priority' },
        { prio: 1, label: 'Priority 1' },
        { prio: 2, label: 'Priority 2' },
        { prio: 3, label: 'Priority 3' },
        { prio: 4, label: 'Priority 4' },
        { prio: 5, label: 'Priority 5' },
        { prio: 6, label: 'Priority 6' },
        { prio: 7, label: 'Priority 7' },
        { prio: 8, label: 'Priority 8' },
        { prio: 9, label: 'Priority 9' },
        { prio: 10, label: 'Priority 10' },
      ],
      selectedPriority: { prio: 0, label: 'Select Priority' },
    };
  },

  computed: {
    areAllSelected() {
      return (
        this.tasks.every((task) => {
          return task.checked;
        }) && this.tasks.length > 0
      );
    },
    areAnySelected() {
      return this.tasks.some(({ checked }) => checked);
    },
    taskClasses(task) {
      const classes = {
        done: task.checked,
        [task.priority.prio]: true,
      };
      console.log(classes);
      return classes;
    },
  },

  methods: {
    addTask() {
      const task = this.newTask.trim();
      const priority = this.selectedPriority;

      if (task) {
        this.tasks.push({ text: task, checked: false, priority });
        this.tasks = this.tasks.sort(
          (a, b) => a.priority.prio - b.priority.prio
        );
        console.log(this.tasks);
        this.newTask = '';
      }
    },

    removeTask(task) {
      const index = this.tasks.indexOf(task);
      this.tasks.splice(index, 1);
    },

    clearList() {
      console.log(this.tasks);
      if (this.areAnySelected) {
        this.tasks = this.tasks.filter(({ checked }) => !checked);
      } else {
        this.tasks = [];
      }
    },

    selectAll() {
      const targetValue = !this.areAllSelected;

      this.tasks.forEach((task) => {
        task.checked = targetValue;
      });
    },
  },
};
</script>

<style>
/* Relevant resets */
ul,
li {
  margin: 0;
  padding: 0;
  border: 0;
}

/* Global Styles */
body {
  line-height: 1;
  font-family: 'Lato', sans-serif;
  background-color: #eff1f2;
}

.container {
  width: 70%;
  margin: 1em auto 3em;
  border: 1px solid #efefef;
}

.panel,
li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  list-style-type: none;
  padding: 10px;
  border-bottom: 1px solid #efefef;
  background-color: #e7e8eb;
}

.text-input {
  border: 1px solid #dedede;
  padding-left: 10px;
  width: 70%;
  height: 35px;
  color: #555;
}

/* TODO update button class */
.btn {
  color: #555;
  background-color: #ffffff;
  border: 1px solid #bbb;
  outline: 0;
  width: 100px;
  height: 38px;
  cursor: pointer;
  font-size: 14px;
}

/* Task  area */

.list li {
  background-color: #244c4e;
}

.list li.low {
  background-color: green;
}

.list li.medium {
  background-color: yellow;
}

.list li.high {
  background-color: hotpink;
}

.list li button {
  background-color: transparent;
  border: 1px solid #3465a4;
  color: #ddd;
  visibility: hidden;
  font-size: 20px;
  font-weight: bold;
}

.list li:hover > button {
  visibility: visible;
}

.list label {
  padding-right: 10px;
  display: inline-block;
  width: 70%;
  font-size: 18px;
  line-height: 24px;
  color: #fcfcfc;
  z-index: 2;
  overflow: hidden;
}

.list li.done label {
  color: #d9d9d9;
  text-decoration: line-through;
}

.center-text {
  text-align: center;
}

/* Instructions and Credit */

.credit {
  margin: 1em auto 5em;
  text-align: center;
  font-size: 13px;
  line-height: 0.6;
  color: #999;
}

.credit a {
  text-decoration: none;
  color: #999;
}

.credit a:hover {
  text-decoration: underline;
}

.hidden {
  display: none;
}

/* Media Queries */

@media screen and (max-width: 768px) {
  .container {
    width: 90%;
    max-width: 90%;
  }

  .text-input,
  .list label {
    width: 60%;
    font-size: 14px;
  }

  /* TODO update button class */
  .btn {
    width: 50px;
    height: 50px;
  }
}

.header {
  display: flex;
  justify-content: center;
}

.priority {
  height: 50px;
}
</style>
