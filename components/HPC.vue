<template>
  <header class="header">
    <div class="parent justify">
      <div class="content" v-for="(user, i) in users" :key="user.HPC">
        <div class="parent" >
          <!-- <aside class="server" v-for="(vm, i) in user.VM" :key="i">
            <div :class="vm.server !== '' ? 'service' : ''">
              <div>{{ vm.server ? vm.server : "" }}</div>
              <div class="vm">{{ vm.name }}</div>
            </div>
          </aside> -->

          <aside  class="server" v-for="(vm, j) in user.VM" :key="j">
            <div :class="vm.server !== '' ? 'service' : ''">
              <div
               @click="alert"
                class="server-row"
                :data-parent-index="i"
                :data-current-index="j"
                draggable="false"
                @dragover="onDragOver($event)"
                @drop="onDragDrop($event)"
                @dragleave="onDragLeave($event)">
                {{ vm.server }}
              </div>
              <div class="vm">{{ vm.name }}</div>
            </div>
          </aside>
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
        <li draggable="true" @dragstart="onDragStart($event) ">
        <!-- <p>periciption </p> -->
        {{ server.server}}  
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

let alert=(e)=>{
  // e.preventDefault();
  alert('popup..')

}
    


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
};

const onDragDrop = (e) => {
  let droppedElement = e.target.closest("div");
  let parentIndex = droppedElement.getAttribute("data-parent-index");
  let currentIndex = droppedElement.getAttribute("data-current-index");

  if (droppedElement.innerText === "") {
    users.value[Number(parentIndex)].VM[Number(currentIndex)].server =draggedElementValue;
    droppedElement.classList.add("server-active");
    // draggedElement.remove();
    droppedElement.classList.remove("service-dragover");
    droppedElement.classList.add("server-row");
  }
};
</script>


<style scoped>

.header {
  display: flex;
  justify-content: space-between;
  height: 80vh;
  /* background-color: rgb(211, 162, 162); */

}
/* .children{
padding-top:20px;
} */
.parent {
  /* background-color: chartreuse; */
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
  flex-direction: row;
}
.justify {
  /* background-color: blueviolet; */
  justify-content: center;
  border: 3px solid green;
  margin-top: 3%;
  padding: 40px 0px;
  width: 84%;
  /* height: 70vh; */
}
.content {
  margin-right: 5px;
  margin-left: 2px;
  margin-bottom: 100px;
  padding-bottom: 100px;
  /* background-color: blueviolet; */
  /* margin-top: 0px; */
  /* padding-top: 40px; */
 
  /* background-color: cornsilk; */
}
.server div {
  height: 20px;
}
.server-active {
  /* background-color: rgb(212, 89, 41); */
  background-color: rgb(151, 234, 151);
  text-align: center;
  /* padding: 5px 1px; */
}
.service-dragover {
  border: 1px dashed green;
}
.server-row {
  border: 1px dashed transparent;
  margin-bottom: 5px;
}
/* .service {
  background-color: rgb(151, 234, 151);
  text-align: center;
} */
.vm {
  /* margin-top: 2px; */
  background-color: gray;
  padding: 10px 16px;
  margin-top: 6px;
 
  /* margin-top: ; */
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
  /* padding-top: 0px; */
  margin-top: 42px;
}
.container-service {
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
  background-color: rgb(151, 234, 151);
  text-align: center;
  padding: 6px 15px;
  width: 100px;
  height: auto;
  /* margin-left: 0px; */
  /* margin-bottom: 2px; */
  cursor: pointer;
}
/* .service-right {
  background-color: rgb(242, 41, 19);
  text-align: center;
  padding: 2px 0px;
  width: 60px;
} */
</style>
