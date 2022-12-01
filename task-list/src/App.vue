<template>
  <v-app>
    <v-app-bar app color="#001F42 dark ">
      <div class="d-flex align-center">
        <v-img
          alt="task list icon"
          class="shrink mr-2"
          contain
          src="../src/assets/checklist_icon.png"
          transition="scale-transition"
          width="40"
        />
      </div>

      <v-btn text>
        <span class="mr-2">Task List app</span>
      </v-btn>
    </v-app-bar>

    <v-main>
      <TaskList />
    </v-main>
  </v-app>
</template>

<script>
import TaskList from './components/TaskList';

export default {
  name: 'App',

  components: {
    TaskList,
  },

  data: () => ({
    //
  }),
};
</script>
