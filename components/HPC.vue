<template>
  <header class="header">
    <div class="parent justify">
      <div class="content" v-for="(user, i) in users" :key="user.HPC">
        <div class="parent">
          <!-- <aside class="server" v-for="(vm, i) in user.VM" :key="i">
            <div :class="vm.server !== '' ? 'service' : ''">
              <div>{{ vm.server ? vm.server : "" }}</div>
              <div class="vm">{{ vm.name }}</div>
            </div>
          </aside> -->
          <aside class="server" v-for="(vm, j) in user.VM" :key="j">
            <div :class="vm.server !== '' ? 'service' : ''">
              <div
                class="server-row"
                :data-parent-index="i"
                :data-current-index="j"
                draggable="true"
                @dragover="onDragOver($event)"
                @drop="onDragDrop($event)"
                @dragleave="onDragLeave($event)"
              >
                {{ vm.server }}
              </div>
              <div class="vm">{{ vm.name }}</div>
            </div>
          </aside>
        </div>
        <div>
          <h3 class="hpc">{{ user.HPC }}</h3>
        </div>
      </div>
    </div>

    <!-- service side -->

    <footer class="container">
      <h2 class="container-service">Service</h2>
      <ul class="server-wrapper" v-for="server in serverdata" :key="server.id">
        <li draggable="true" @dragstart="onDragStart($event)">
          {{ server.server }}
        </li>
      </ul>
    </footer>
  </header>
</template>

<script setup>
import userData from "./user.json";
import serverdata from "./server.json";
import draggable from "vuedraggable";
import { ref } from "vue";

let users = ref(userData);
let draggedElement = ref("");
let draggedElementValue = ref("");

const onDragStart = (e) => {
  // e.preventDefault();
  draggedElement = e.target.closest("li");
  draggedElementValue = e.target.closest("li").innerText;
  // console.log("start", e.target.closest("li").innerText);
};

const onDragOver = (e) => {
  e.preventDefault();
  let dragOverElement = e.target.closest("div");
  dragOverElement.classList.remove("server-row");
  dragOverElement.classList.add("service-dragover");
  // console.log("over", e.target.closest("div"));
};
const onDragLeave = (e) => {
  e.preventDefault();
  let dragOverElement = e.target.closest("div");
  dragOverElement.classList.remove("service-dragover");
  dragOverElement.classList.add("server-row");

  // console.log("over", e.target.closest("div"));
};

const onDragDrop = (e) => {
  let droppedElement = e.target.closest("div");
  let parentIndex = droppedElement.getAttribute("data-parent-index");
  let currentIndex = droppedElement.getAttribute("data-current-index");

  if (droppedElement.innerText === "") {
    users.value[Number(parentIndex)].VM[Number(currentIndex)].server =
      draggedElementValue;
    droppedElement.classList.add("server-active");
    draggedElement.remove();
    droppedElement.classList.remove("service-dragover");
    droppedElement.classList.add("server-row");
  }
};
</script>

<style scoped>
/* ul {
}
li {
} */
.service-dragover {
  border: 1px dashed green;
}
.server-row {
  border: 1px dashed transparent;
}
.header {
  display: flex;
  justify-content: space-between;
  height: auto;
}
.parent {
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
  flex-direction: row;
}
.justify {
  justify-content: center;
  border: 3px solid green;
  margin-top: 3%;
  padding: 40px 0px;
  width: 84%;
}
.content {
  margin-right: 5px;
  margin-left: 2px;
  margin-top: 40px;
}
.server div {
  height: 20px;
}
.server-active {
  background-color: rgb(151, 234, 151);
}
/* .service {
  background-color: rgb(151, 234, 151);
  text-align: center;
} */
.vm {
  margin-top: 7px;
  background-color: gray;
  padding: 5px 16px;
}
.hpc {
  background-color: rgb(240, 180, 102);
  text-align: center;
  padding: 15px;
  margin-top: 42px;
}
.container {
  border: 3px solid green;
  width: 200px;
  padding-top: 0px;
  margin-right: 20px;
  margin-top: 50px;
}
.container-service {
  padding-left: 5px;
  text-align: center;
}
/* .server-user {
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
} */
.server-wrapper {
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
}
.server-wrapper li {
  list-style: none;
  background-color: aqua;
  padding: 5px 16px;
  width: 30px;
  margin-bottom: 2px;
  cursor: pointer;
}
.service-right {
  background-color: rgb(98, 226, 98);
  text-align: center;
  padding: 2px 0px;
  width: 60px;
}
</style>
