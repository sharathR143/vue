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

          <div class="server" v-for="(vm, j) in user.VM" :key="j">
            <!-- <div class="service"> -->
            <div :class="vm.server !== '' ? 'service' : ''">
              <div
                class="server-row"
                :data-parent-index="i"
                :data-current-index="j"
                @click="vm.server !== '' ? showRemove($event) : ''"
                draggable="false"
                @dragover="onDragOver($event)"
                @drop="onDragDrop($event)"
                @dragleave="onDragLeave($event)"
              >
                {{ vm.server }}
                <span
                  class="d-none remove-Button"
                  @click="remove($event, i, j)"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    height="15"
                    viewBox="0 -960 960 960"
                    width="15"
                  >
                    <path
                      d="m256-200-56-56 224-224-224-224 56-56 224 224 224-224 56 56-224 224 224 224-56 56-224-224-224 224Z"
                    />
                  </svg>
                </span>
              </div>
              <div class="vm">{{ vm.name }}</div>
            </div>
          </div>
        </div>
        <main>
          <h3 class="hpc">{{ user.HPC }}</h3>
        </main>
      </div>
    </div>

    <!-- service side -->

    <footer class="container">
      <h2 class="container-service">Service</h2>
      <ul class="server-wrapper" v-for="server in serverdata" :key="server.id">
        <li draggable="true" @dragstart="onDragStart($event)">
          <p>periciption</p>
          <p>{{ server.server }}</p>
        </li>
      </ul>
    </footer>
  </header>
</template>

<script setup>
import userData from "./user.json";
import serverdata from "./server.json";
// import draggable from "vuedraggable";
import { ref } from "vue";

let users = ref(userData);
let draggedElement = ref("");
let draggedElementValue = ref("");

const showRemove = (e) => {
  e.preventDefault();
  let tragetElement = e.target.children[0];
  tragetElement.classList.remove("d-none");
};

let remove = (e, parentIndex, childIndex) => {
  e.preventDefault();
  let tragetElement = e.target.closest("div");
  let tragetCloseTag = e.target.closest("span");
  users.value[Number(parentIndex)].VM[Number(childIndex)].server = "";
  tragetCloseTag.classList.add("d-none");
  tragetElement.classList.remove("server-active");
};

const onDragStart = (e) => {
  // e.preventDefault();
  draggedElement = e.target.closest("li");
  draggedElementValue = e.target.closest("li").lastChild.innerText;
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
};

const onDragDrop = (e) => {
  let droppedElement = e.target.closest("div");
  let parentIndex = droppedElement.getAttribute("data-parent-index");
  let currentIndex = droppedElement.getAttribute("data-current-index");

  if (droppedElement.innerText === "") {
    users.value[Number(parentIndex)].VM[Number(currentIndex)].server =
      draggedElementValue;
    droppedElement.classList.add("server-active");
    droppedElement.classList.remove("service-dragover");
    droppedElement.classList.add("server-row");
    // draggedElement.remove();
  }
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  height: 80vh;
}
.d-none {
  display: none;
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
  margin-bottom: 100px;
  padding-bottom: 100px;
}
.server div {
  height: 20px;
  cursor: pointer;
}
.server-active {
  background-color: rgb(151, 234, 151);
  text-align: center;
}
.service-dragover {
  border: 1px dashed green;
}
.server-row {
  border: 1px dashed transparent;
  margin-bottom: 5px;
  position: relative;
}
.remove-Button {
  position: absolute;
  top: -17px;
  right: 0px;
}
.service {
  background-color: rgb(151, 234, 151);
  text-align: center;
}
.vm {
  background-color: gray;
  padding: 6px 16px;
  margin-top: 6px;
}
.hpc {
  background-color: rgb(240, 180, 102);
  text-align: center;
  padding: 15px;
  margin-top: 55px;
}
.container {
  border: 3px solid green;
  width: 200px;
  margin-top: 42px;
  overflow-y: auto;
}
.container-service {
  text-align: center;
}

.server-wrapper {
  display: flex;
  flex-direction: column;
}
.server-wrapper li {
  list-style: none;
  background-color: rgb(151, 234, 151);
  text-align: center;
  padding: 6px 15px;
  width: 100px;
  height: auto;
  cursor: pointer;
}
/* .server-user {
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
} */
/* .service-right {
  background-color: rgb(242, 41, 19);
  text-align: center;
  padding: 2px 0px;
  width: 60px;
} */
</style>
