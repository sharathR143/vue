<template>
  <header class="header">
                  <!-- service side -->
     <footer class="container">
      <h2 class="container-service">Service</h2>
      <ul class="server-wrapper" v-for="server in serverdata" :key="server.id">
        <li draggable="true" @dragstart="onDragStart($event)">
          <p>{{ server.name }}</p>
          <p>{{ server.server }}</p>
        </li>
      </ul>
    </footer>

            <!-- HPC AND VM AND SERVICE SIDE -->
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
                @click="vm.server !== '' ? showRemove($event) : '' "
                @dblclick="vm.server !== '' ? showClosed($event) :'' "
               
                draggable="true"
                @dragover="onDragOver($event)"
                @drop="onDragDrop($event)"
                @dragleave="onDragLeave($event)"
              >
               <!-- <h3> </h3> -->
               {{ vm.server }}
                <span
                  class="d-none remove-Button svg"
                  @click="remove($event, i, j)"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 -960 960 960"
                    class="svg-class">
                    <path
                      d="m256-200-56-56 224-224-224-224 56-56 224 224 224-224 56 56-224 224 224 224-56 56-224-224-224 224Z"
                    />
                  </svg>
                </span>
              </div>
              <div ><h3 class="vm">{{ vm.name }}</h3></div>
            </div>
          </div>
        </div>
        <main>
          <h3 class="hpc">{{ user.HPC }}</h3>
        </main>
      </div>
    </div>


   

  </header>
</template>

<script setup>
import userData from "./user.json";
import serverdata from "./server.json";
import { ref } from "vue";

let users = ref(userData);
let draggedElement = ref("");
let draggedElementValue = ref("");

const showRemove = (e) => {
  e.preventDefault();
  let targetElement = e.target.children[0];
  targetElement.classList.remove("d-none");
};
const showClosed = (e) => {
  e.preventDefault();
  let targetElement = e.target.children[0];
  targetElement.classList.add("d-none");
};


let remove = (e, parentIndex, childIndex) => {
  e.preventDefault();
  let targetElement = e.target.closest("div");
  let targetCloseTag = e.target.closest("span");
  users.value[Number(parentIndex)].VM[Number(childIndex)].server = "";
  targetCloseTag.classList.add("d-none");
  targetElement.classList.remove("server-active");
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
.svg{
  background-color: rgb(182, 196, 209);
  border-radius: 10px 50px;
  border-radius: 2px;
  height: 18px;
  width: 16px;
}
.svg-class{
  height: 16px;
  width: 16px;
  margin-top: 1px;
}
.remove-Button {
  position: absolute;
  top: -20px;
  right: -5px;
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
  padding: 20px 0px;
  width: 87%;
}
.content {
  margin-right: 5px;
  margin-left: 2px;
  margin-bottom: 50px;
  margin-top: 10px;
  padding-bottom: 100px;
}
.server div {
  height: 20px;
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
  padding: 5px 3px;
  cursor: pointer;
}
.service {
  background-color: rgb(151, 234, 151);
  text-align: center;
}
.vm {
  background-color: rgb(220, 209, 209);
  padding: 6px 23px;
  font-family:  Times, serif;
  margin-top: 10px;
}
.hpc {
  background-color: rgb(240, 180, 102);
  text-align: center;
  padding:17px 15px;
  margin-top: 68px;
  font-family:  Times, serif;
}
.container {
  border: 3px solid green;
  width: 180px;
  background-color: blueviolet;
  margin-top: 42px;
  /* overflow-y: auto; */
  /* height: 600px; */
}
.container-service {
  text-align: center;
  background-color: aqua;
}

.server-wrapper {
  display: flex;
  flex-direction: column;
}
.server-wrapper li {
  display: flex;
  justify-content:space-evenly;
  background-color: rgb(208, 184, 158);
  text-align: center;
  margin-bottom: 40px;
  width: 130px;
  cursor: pointer;
  list-style: none;
}
.server-wrapper  p {
  background-color: blueviolet; 
  /* margin: 10px; */
}

</style>
