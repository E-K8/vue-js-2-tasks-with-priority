<template>
  <v-container>
    <div class="np-priority-select">
      <label for="cars">Display tasks by priority:</label>
      <select
        @change="updateList()"
        name="priority"
        id="priority"
        class="np-priority-select-input"
        v-model="selectedPriority"
      >
        <option value="All">All</option>
        <option value="Priority 1">Priority 1</option>
        <option value="Priority 2">Priority 2</option>
        <option value="Priority 3">Priority 3</option>
        <option value="Priority 4">Priority 4</option>
        <option value="Priority 5">Priority 5</option>
        <option value="Priority 6">Priority 6</option>
        <option value="Priority 7">Priority 7</option>
        <option value="Priority 8">Priority 8</option>
        <option value="Priority 9">Priority 9</option>
        <option value="Priority 10">Priority 10</option>
      </select>
    </div>

    <div class="np-list-item">
      <div class="np-ib np-ib-item np-ib-item__head">ID</div>
      <div class="np-ib np-ib-item np-ib-item__head">Task</div>
      <div class="np-ib np-ib-item np-ib-item__head">Priority</div>
    </div>
    <div v-for="(item, i) in sortedListItems" :key="i" class="np-list-item">
      <div class="np-ib np-ib-item">
        {{ item.id }}
      </div>
      <div class="np-ib np-ib-item">
        {{ item.task }}
      </div>
      <div class="np-ib np-ib-item">
        {{ item.priority }}
      </div>
    </div>
  </v-container>
</template>

<script>
const listItems = [
  {
    id: 0,
    task: 'Walk 9k',
    priority: 'Priority 2',
  },
  {
    id: 1,
    task: 'Exercise',
    priority: 'Priority 3',
  },
  {
    id: 2,
    task: 'freeCodeCamp',
    priority: 'Priority 1',
  },
  {
    id: 3,
    task: 'GitHub',
    priority: 'Priority 2',
  },
  {
    id: 4,
    task: 'Codewars',
    priority: 'Priority 3',
  },
  {
    id: 5,
    task: 'Volunteer',
    priority: 'Priority 8',
  },
  {
    id: 6,
    task: 'Email teammate',
    priority: 'Priority 3',
  },
  {
    id: 7,
    task: 'Redo CV',
    priority: 'Priority 4',
  },
  {
    id: 8,
    task: 'Update LinkedIn',
    priority: 'Priority 4',
  },
  {
    id: 9,
    task: 'Research VueJS',
    priority: 'Priority 1',
  },
];

export default {
  name: 'TaskList',
  data() {
    return {
      listItems: listItems,
      sortedListItems: listItems,
      selectedPriority: 'All',
    };
  },
  mounted() {
    this.sortedListItems = this.listItems;
  },
  methods: {
    updateList() {
      this.sortedListItems = [];
      this.sortedListItems =
        this.selectedPriority === 'All'
          ? (this.sortedListItems = listItems)
          : listItems.filter((item) => item.priority === this.selectedPriority);
    },
  },
};
</script>

<style>
v-container {
  padding: 12px 16px;
  max-width: 430px;
}
.np-list-item {
  border-bottom: 1px solid rgb(231, 231, 231);
}
.np-ib {
  display: inline-block;
}
.np-ib-item {
  min-width: 130px;
  padding: 6px;
}
.np-ib-item__head {
  font-weight: 600;
  color: #001f42;
}
.np-priority-select {
  margin: 4px 0px 20px 0px;
}
.np-priority-select-input {
  min-width: 120px;
  margin-left: 10px;
  outline: none;
  border: 1px solid #001f42;
  font-size: 16px;
  background: #001f42;
  color: #ffffff;
  border-radius: 4px;
  padding: 3px;
}
.np-credits {
  font-size: 12px;
  margin-top: 12px;
}
</style>
