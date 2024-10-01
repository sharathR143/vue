

 
<template>
  <div class="w-[900px] xl:w-[550px] 1xl:w-[550px] 2xl:w-[575px] 3xl:w-[700px] h-[400px] xl:h-[390px] 1xl:h-[500px] 2xl:h-[550px] 3xl:h-[740px] rounded-lg"  style="background-color:#EFF2EF;">
    <header class="flex justify-between mt-0 ml-5">
        <div>
          <p class="font-bold px-5 py-5 xl:text-[17px] 1xl:text-[17px] 3xl:text-[19px] uppercase text-[#992121]">Service Location</p>
        </div>
      </header>

    <aside  class="mr-5 xl:h-[250px] 1xl:h-[380px] 2xl:h-[420px] 3xl:h-[580px]  mx-10 rounded-lg  xl:mt-3 1xl:mt-3 2xl:mt-5" style="background-color:#FFFFFF">
      <div class="bg-red-00 h-[30px] flex">
        <p class="text-[18px] ml-4  font-bold mt-2">BMS Information</p>
      </div>

      <div class="flex justify-evenly mr-5 xl:h-[250px] 1xl:h-[290px] 2xl:h-[380px]   mx-10 rounded-lg  xl:mt-3 1xl:mt-3 2xl:mt-5">
        <div class="flex gap-2 items-end  border-red-300 h-[300px]  3xl:h-[400px] mt-[15px]">
         
            <div v-if="selectedName== 'parking'"  class="flex gap-2 items-end bg-red-00  3xl:w-[460px] ">
              
            <div class="bg-white 3xl:ml-[20px]   cursor-pointer">
              <div class="h-[270px]      2xl:overflow-auto  3xl:overscroll-none  bg-gray-00    bg-yellow-00">
                 <div class="flex gap-2 items-end justify-center px-[20px] h-[250px]  bg-gray-00  mb-5">
                  <div v-for="host in hostnames" :key="host">
                     <div v-for="ParkingData in filteredParkingData" :key="ParkingData">
                      <div class="mb-4" v-if="ParkingData.config['Hostname'] == host">
                        <div v-for="name in ParkingData.names" :key="name" class="px-[5px] py-[5px] 3xl:px-[10px]  3xl:py-[10px] mx-5 border-dashed border-black border-1 ele  bg-blue-300 text-center  transition delay-400 duration-030 ease-in-out">
                          {{ name }}
                        </div>
                      </div>
                    </div>
                    
                    <div class="1xl:px-[10px]  1xl:py-[5px] 2xl:px-[15px]  2xl:py-[10px] 3xl:px-[10px]  3xl:py-[10px]  3xl:w-[80px] mx-5  border-dashed border-blue-400  bg-gray-300 border-2 text-center" v-if="host === 'ZONAL'">
                       {{ host }}
                       </div>
                       <div class="1xl:px-[10px]  1xl:py-[5px] 2xl:px-[15px]  2xl:py-[10px]  3xl:px-[10px]  3xl:py-[10px] 3xl:w-[80px] mx-5  border-dashed border-blue-400 border-2 text-center" v-else>
                        {{ host }}
                      </div>
                    </div>
                  </div> 

           </div>
          </div>
          </div>


          <div v-else  class="flex gap-2 items-end 3xl:w-[380px] bg-red-00">
            <div v-for="host in hostnames" :key="host">
                  <div v-for="drivingData in filteredDrivingData" :key="drivingData">
                    <div class="mb-4  " v-if="drivingData.config['Hostname'] == host">
                      <div v-for="name in drivingData.names" :key="name" class="px-[5px] py-[5px] 3xl:px-[10px]  3xl:py-[10px] mx-5 border-dashed border-1 border-black text-center ele bg-blue-300">
                        <span class="">{{ name }}</span>
                      </div>
                    </div>
                  </div>
                  
                  <div class="bg-white mb-5 flex justify-end  items-end ">
                    <div class="1xl:px-[10px]  1xl:py-[5px] 2xl:px-[15px]  2xl:py-[10px] 3xl:px-[10px]  3xl:py-[10px]  3xl:w-[80px] mx-5 border-dashed border-blue-400   bg-gray-300 border-2 "   v-if="host === 'ZONAL'">
                      <span class="capitalize  text-center">{{ host }}</span>
                    </div>
                    <span class=" 1xl:px-[10px]  1xl:py-[5px] 2xl:px-[15px]  2xl:py-[10px]  3xl:px-[10px] text-center 3xl:py-[10px]  3xl:w-[80px] mx-5 border-dashed border-blue-400 border-2 " v-else>
                      {{ host }}
                    </span>
                  </div>
                </div>
          </div>

         
      </div>
      </div>
    </aside>
  </div>
</template> 


 <script setup>
import { computed } from "vue";
import driving from "../../data/container-Driving.json";
import parking from "../../data/container-parking.json";

const json = ref(driving);
const parkingJson = ref(parking);


const filteredDrivingData = json.value.containers.filter((element) => {
  return element.annotation["piccolo.package.name"] == "bms";
});

const filteredParkingData = parkingJson.value.containers.filter((element) => {
  return element.annotation["piccolo.package.name"] == "bms";
});

const props = defineProps(["drivingjson", "selected","selectedName"]);

const hostnames = ["SOC0", "SOC1", "ZONAL"];


</script>


<style scoped>


.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}
.list-enter-active, .list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from, .list-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
.list-enter-to, .list-leave-from {
  opacity: 1;
  transform: translateY(0);
}
/* Fade transition effect */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}


.ele {
  transition: opacity 3s cubic-bezier(0.4, 0, 0.2, 1);
  opacity: 10;
  animation: fadeIn 3s forwards; 
}



@keyframes fadeIn {
  0% {
    opacity: 0;
  }
 
  100% {
    opacity: 1;
  }
}
</style>

