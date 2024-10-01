<template>
    <main>
        <!-- <button @click="closeScenario" class="close-button">Close</button> -->
        <!-- scenario  -->
        <aside class="flex justify-evenly py-4 mx-4 rounded-lg bg-white">
            <div>
                <img src="/img/car.png" alt="parking image" class="w-[150px] rounded-lg  h-[100px]"> 
                <div class="flex justify-center">
                    <p>Driving</p>
                </div> 
            </div>
            
            <div>
                <img src="/img/car1.png" alt="parking image" class="w-[150px] rounded-lg  h-[100px]"> 
                <div class="flex justify-center">
                    <p>Parking</p> 
                </div>
            </div>

            <div>
                <img src="/img/charging.png" alt="parking image" class="w-[150px] rounded-lg  h-[100px]"> 
                <div class="flex justify-center">
                    <p>Charging</p> 
                </div>
            </div>

            <div>
                <img src="/img/lowbattery.png" alt="parking image" class="w-[150px] rounded-lg  h-[100px]"> 
                <div class="flex justify-center">
                    <p>Low Battery</p> 

                </div>
            </div>

        </aside>

        <!-- host Name drag value section -->
        <aside class="mt-5 py-4 mx-4 rounded-lg bg-white ">
            <div class="flex justify-center items-center">
                <div v-for="containerName in dragelement" :key="containerName"  >
                <p class="flex justify-center items-center text-center bg-gray-300 border-black/20 border-solid  border-2 my-2 px-5 py-2 mx-3  " v-if="containerName=='camera' || containerName=='location' || containerName=='DSM'">{{ containerName }}</p>
                <p class="flex justify-center items-center text-center bg-blue-300 border-black/20 border-solid  border-2 my-2 px-5 py-2 mx-3  " v-else>{{ containerName }}</p>

            </div> 
            </div>
        </aside>


        
        <aside class="mt-5 py-4 mx-4 rounded-lg bg-white h-[130px] ">
            <header class="flex  bg-red-00 justify-center items-center mb-5">
                <!-- host Name drop value -->
                 <div class="flex justify-center items-center px-2 py-2 mx-5">
                    <div class="px-3 py-2 mx-5 bg-blue-300"></div>
                    <div class="px-3 py-2 mx-5 bg-blue-300"></div>

                    <div class="px-3 py-2 mx-5 bg-blue-300"></div>

                </div>
            </header>
                <!-- host Name key sections -->
            <section class="flex  bg-red-00 justify-center items-center ">
                <div></div>
                <div v-for="host in hostnames" :key='host'>
                    <div class="px-3 py-2 mx-5 bg-blue-300">{{ host }}</div>
                </div>
            </section>
        </aside>


        <footer>
            <div class="flex justify-end  pt-3">
                <button class="px-2 py-2  mx-[10px] rounded-md w-[100px]  text-sm   text-white   bg-gradient-to-r from-green-400 to-green-600  hover:from-green-500 hover:to-green-700  transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5  shadow-green-500/50 " @click="createTemplate">Create</button>
                <button class="px-2 py-2  mx-[10px] rounded-md w-[100px]  text-sm   text-white   bg-gradient-to-r from-red-400 to-red-600  hover:from-red-500 hover:to-red-700  transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5  shadow-red-500/50 " @click="cancelTemplate">Cancel</button>
            </div>
        </footer>
    </main>
</template>

<script setup>
import {ref} from 'vue';

const dragelement=ref(["rdv",'camera','location','mavd','frism','DSM','bils'])
console.log(dragelement.value)

import { defineEmits } from 'vue'
  
//   const emit = defineEmits(['close'])
  
//   const closeScenario = () => {
//     emit('close')
//   }


const hostnames=ref(['soc0','soc1','zonal'])

</script>


<style scoped>
.piccolo-scenario {
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.close-button {
  margin-top: 10px;
  padding: 5px 10px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}
</style>
