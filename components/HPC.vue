<template>
  <header class="header">
                  <!-- service side -->
     <footer class="container">
      <h2 class="container-service">Service</h2>
     <!-- <div class="container-div"> -->
      <ul class="server-wrapper" v-for="server in serverdata" :key="server.id">
        <li draggable="true" @dragstart="onDragStart($event)" class="li">
          <a>{{ server.name }}</a>
          <a>{{ server.server }}</a>
        </li>
      </ul>
     <!-- </div> -->
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
                @dblclick="vm.server !== '' ? showRemove($event) : '' "
                @click="vm.server !== '' ? showClosed($event) :'' "
               
                draggable="false"
                @dragover="onDragOver($event)"
                @drop="onDragDrop($event)"
                @dragleave="onDragLeave($event)"
              >
               
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
  height: 84vh;
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
  padding: 30px 0px;
  width: 87%;
}
.content {
  margin-right: 5px;
  margin-left: 2px;
  margin-bottom: 80px;
  margin-top: 20px;
}
.server div {
  height: 20px;
  padding: 6px 0px;
}
.server-active {
  /* background-color: rgb(95, 172, 95); */
  /* background-color: rgb(151, 212, 151); */
  background-color: #e0aaff;
  text-align: center;
}
.service-dragover {
  border: 2px dashed green;
}
.server-row {
  border: 1px dashed transparent;
  margin-bottom: 4px;
  font-size: 18px;
  font-weight: 550;
  position: relative;
  cursor: pointer;
}
.service {
  text-align: center;
}
.vm {
  /* background-color: rgb(220, 209, 209); */
  background-color: rgb(195, 187, 187);
  padding: 7px 23px;
  font-family:  Times, serif;
  font-size: 18px;
  font-weight: 550;
  margin-top: 1px;
}
.hpc {
  /* background-color: rgb(240, 180, 102); */
   background-color: rgb(241, 196, 128); 
  text-align: center;
  padding:17px 15px;
  font-size: 18px;
  font-weight: 550;
  margin-top: 65px;
  font-family:  Times, serif;
}
.container {
  border: 3px solid green;
  width: 180px;
  padding-right: 0px;
  margin-top: 42px;
  /* background-color: rgb(191, 176, 206); */
  /* overflow-y: auto; */
  /* height: 600px; */
}


.server-wrapper {
   display: flex;
  flex-direction: column;
  justify-content: start;

}

.container-service {
  text-align: center;
  font-size: 28px;
}


.li{
  display: flex;
  justify-content:space-between;
  /* background-color: rgb(133, 204, 133); */
 /* background-color: #d29cdc; */
  /* background-color: #d29cdc; */
  background-color: rgb(151, 212, 151);
  /* background-color: #e0aaff; */
  border-radius: 1px;
  margin-top: 10px;
  padding-top: 2px;
  margin-left: 0px;
  padding-left: 4px;
  padding-right: 1px;
  align-items: center;
  width: 110px;
  height: 42px;
  cursor: pointer;
  list-style: none;
}

.li a{
  margin: 14px 5px;
}

</style>
