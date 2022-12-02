<template>
  <v-container>
    <section class="panel">
      <input type="checkbox" />
      <input
        type="text"
        v-model="newTask"
        @keyup.enter="addTask"
        placeholder="Enter a new task"
        class="text-input"
      />
    </section>
  </v-container>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {};
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
  background-color: #3465a4;
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
