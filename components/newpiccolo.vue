


  <template>
    <main class="bg-white mt-10  py-5  3xl:px-[10px] 3xl:mt-5 rounded-lg  xl:w-[1200px] 1xl:w-[1280px] 2xl:w-[1460px] 3xl:w-[1830px] xl:ml-[-60px] 1xl:ml-[-100px] 2xl:ml-[-190px] 3xl:ml-[-60px]  3xl:h-[900px]">
      <div>
        <h1 class="font-bold  uppercase  mb-[10px]  pl-5 text-[#992121]  text-[20px] 1xl:text-[17px] 3xl:text-[23px]">PICCOLO Design studio</h1>
      </div>

      
      <!-- flex justify-center items-center -->
      <div class="flex">
        <aside  class="container pt-10  rounded-lg  ml-5  1xl:h-[500px] 2xl:h-[550px] pb-10  1xl:w-[680px] 2xl:w-[800px]  3xl:w-[1000px] 3xl:h-[740px]  " style="background-color:#EFF2EF;">
          <div class="pr-2 mt-[0px] cursor-pointer ml-4  bg-red-00 relative left-[-10px] top-[-30px]  w-[25px]">
            <v-icon color="primary" >mdi-plus</v-icon>
          </div>

          <main class="flex  justify-evenly  bg-red-00 mr-5 ">
            <!-- Driving -->
             <div class=" bg-white cursor-pointer 1xl:w-[280px] border-2 border-blue-500 2xl:w-[300px]  3xl:w-[380px] 3xl:h-[600px] " 
             :class="['bg-white cursor-pointer', { 'border-4 border-red-500  rounded-lg': selectedSection === 'driving' }]"
           
              @click="sendData($event, filteredDrivingData,'driving')"
              @dblclick="unselectSection()">

              <div v-if="showArrow && selectedSection === 'driving'" class="absolute top-[60px] left-[260px]  3xl:left-[400px] transform -translate-x-1/2 text-4xl text-red-500 arrow-animation">
                <img src="/img/Animation-arrow.gif" alt="Driving image" class="w-[100px] h-[100px] mx-2 mt-3  2xl:w-[100px] 3xl:w-[100px] 3xl:h-[100px]  rounded-lg 2xl:h-[100px]">  

              
            </div>
            <!-- ↓ -->
              <div class="mb-5 bg-gray-00">
                <img src="/img/car.png" alt="Driving image" class="w-[260px] mx-2 mt-3  2xl:w-[280px] 3xl:w-[360px] 3xl:h-[250px]  rounded-lg h-[150px] 2xl:h-[200px]">  
                <p class="flex justify-end mr-3  font-bold">Driving</p>
              </div>
              

              <aside class="xl:mt-6 1xl:mt-5 2xl:mt-1  3xl:mt-[50px]   3xl:ml-[px]">
               <div class=" bg-red-00  ml-[80px] xl:ml-[100px] 1xl:ml-[60px]  2xl:ml-[80px] 3xl:ml-[105px] mb-1">
                    <div class="flex justify-center items-center h-[20px]  1xl:h-[30px]  bg-blue-300  xl:w-[70px]  1xl:w-[60px]  2xl:w-[50px] 3xl:w-[60px] mx-10 px-7 py-3  ml-">
                         <p class="">rdv</p>
                    </div>
               </div>
               <div class=" bg-red-00  ml-[80px] xl:ml-[100px]  1xl:ml-[60px] 2xl:ml-[80px] 3xl:ml-[105px] mb-1">
                   <div class="flex  justify-center items-center h-[20px]  1xl:h-[30px]  bg-blue-300   xl:w-[70px] 1xl:w-[60px] 2xl:w-[50px]  3xl:w-[60px]  mx-10 px-7 py-3 ml-">
                    <p class="">mavd</p>
                    </div>
                </div>
                <div class="bg-red-00  ml-[80px] xl:ml-[100px] 1xl:ml-[60px]  2xl:ml-[80px] 3xl:ml-[105px] mb-1">
                    <div class="flex justify-center items-center  h-[20px]  1xl:h-[30px]  bg-blue-300  xl:w-[70px] 1xl:w-[60px] 2xl:w-[50px] 3xl:w-[60px]  mx-10 px-7 py-3 ml-">
                        <p class="">frism</p>
                    </div>
                </div>
                <div class=" bg-red-00  ml-[80px] xl:ml-[100px] 1xl:ml-[60px]  2xl:ml-[80px] 3xl:ml-[105px]">
                    <div class="flex justify-center items-center  h-[20px]  1xl:h-[30px]  bg-blue-300   xl:w-[70px] 1xl:w-[60px] 2xl:w-[50px]  3xl:w-[60px]  mx-10 px-7 py-3 ml-">
                         <p class="">blis</p>
                        </div>
                    </div>
                <div class="flex h-[60px] bg-red-00 w-[100px] ml-[80px] mt-2 1xl:mt-5 xl:ml-[10px] 1xl:ml-[22px] 2xl:ml-[40px] ">
                    <div class="flex justify-center items-center">

                        <div class="text-center border-dashed border-2 border-sky-500   w-[120px]  xl:w-[70px] 1xl:w-[60px] 2xl:w-[60px] 2xl:px-1 1xl:px-1  1xl:py-1 2xl:py-2  mr-4 3xl:w-[80px]   "  style="background-color:#FFFFFF" >
                            <p class="">SOC 0</p>
                        </div>

                        <div  class="text-center border-dashed border-2 border-sky-500  w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[60px]  2xl:px-1 1xl:px-1  1xl:py-1 2xl:py-2 mr-4   3xl:w-[80px] "  style="background-color:#FFFFFF">
                            <p class=" ">SOC 1</p>
                        </div>

                        <div  class="text-center border-dashed border-2 border-sky-500 bg-gray-300 w-[120px] xl:w-[60px] 1xl:w-[60px] 2xl:w-[60px]  1xl:px-1  1xl:py-1 2xl:px-1  2xl:py-2 mr-4    3xl:w-[80px] ">
                            <p class="">ZONAL</p>
                        </div>
                    </div>
                </div>
               </aside>
            </div> 


 

          

          
           <div class="bg-white ml-5  cursor-pointer border-2 border-blue-500 1xl:w-[280px]  2xl:w-[300px]  3xl:w-[380px] 3xl:h-[600px]  3xl:ml-[40px]"
           :class="['bg-white ml-5 cursor-pointer', { 'border-4 border-red-500  rounded-lg ': selectedSection === 'parking' }]" 
            @click="sendData($event, filteredParkingData,'parking')" @dblclick="unselectSection()">

            <div v-if="showArrow && selectedSection === 'parking'" class="absolute   top-[70px] 1xl:left-[600px] 2xl:left-[650px] 3xl:left-[900px] transform -translate-x-1/2 text-4xl text-red-500 arrow-animation ">
              <!-- <span class="animate-bounce w-6 h-6">↓</span> -->
              <img src="/img/Animation-arrow.gif" alt="Driving image" class="mx-2 mt-3 w-[100px] h-[100px]   2xl:w-[100px] 2xl:h-[100px] 3xl:w-[100px] 3xl:h-[100px]  rounded-lg  ">  

            </div>

            <div class="mb-5 bg-green-00">
              <img src="/img/car1.png" alt="parking image" class="w-[260px] mx-2 mt-3  rounded-lg  2xl:w-[280px] h-[150px] 2xl:h-[200px]   3xl:w-[360px] 3xl:h-[250px]">  
              <p class="flex justify-end mr-3 font-bold">Parking</p>
            </div>


           
           <aside class="mt-16 1xl:pt-[38px] 2xl:pt-[40px]  3xl:pt-[75px]  3xl:ml-5">
            <div class="flex  bg-red-00  w-[1200px] h-[40px] bg-red-00  ">

                 <div class="flex justify-center items-center bg-blue-300 w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[60px] 3xl:w-[70px]  h-[20px]  1xl:h-[40px]   ml-[80px] xl:ml-[40px] 1xl:ml-[22px] 2xl:ml-[40px] 3xl:ml-[35px]  ">
                      <p class=" ">blis</p>
                 </div>
                 <div  class="flex justify-center items-center  bg-blue-300 w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[60px] 3xl:w-[70px] h-[20px]  1xl:h-[40px] ml-[80px] xl:ml-[40px]  1xl:ml-[90px] 2xl:ml-[90px]  3xl:ml-[120px]  ">
                      <p class="">frism</p>
                 </div>
             
             </div>
             
              <div class="flex  h-[60px] bg-red-00 w-[100px] ml-[80px]  mt-3 1xl:mt-5 xl:ml-[20px] 1xl:ml-[22px] 2xl:ml-[40px] 3xl:ml-[30px]">
                 <div class="flex justify-center items-center">

                     <div class="text-center border-dashed border-2 border-sky-500   w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[60px]  3xl:w-[80px] 1xl:px-1  1xl:py-1 2xl:px-1  2xl:py-2 mr-4  "  style="background-color:#FFFFFF" >
                         <p class="">SOC 0</p>
                     </div>

                     <div  class="text-center border-dashed border-2 border-sky-500  w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[60px] 3xl:w-[80px] 1xl:px-1  1xl:py-1 2xl:px-1  2xl:py-2  mr-4 "  style="background-color:#FFFFFF">
                         <p class="">SOC 1</p>
                     </div>

                     <div  class="text-center border-dashed border-2 border-sky-500 bg-gray-300 w-[120px] xl:w-[80px] 1xl:w-[60px] 2xl:w-[60px]  3xl:w-[80px] 1xl:px-1  1xl:py-1 2xl:px-1  2xl:py-2   mr-4  ">
                         <p class="">ZONAL</p>
                     </div>
                 </div>
             </div>
     </aside>
         
          </div>
        </main>
      </aside>


       <aside>
        <Servicelocation :drivingjson="propsData" :selected="selected" :selectedName="selectedSection" class="relative top-[-420px] left-[25px] xl:top-[-10px] xl:left-[30px]  1xl:top-[0px] 1xl:left-[10px]  2xl:top-[0px] 2xl:left-[20px]  3xl:left-[70px]" />
      </aside> 

      

    </div>
  </main> 
  </template>
  
 

  <!-- <script setup>
  import { ref, onMounted } from 'vue';
  import Servicelocation from "../mco/service-location.vue";
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
  
  const hostnames = ["SOC0", "SOC1", "ZONAL"];
  
  let propsData = ref(filteredDrivingData);
  
  const selected = ref(false);
  const selectedSection = ref('');
  const showArrow = ref(false);
  const arrowDirection = ref('right');
  
  const sendData = (event, data, section) => {
    console.log("click");
    arrowDirection.value = section === 'parking' ? 'right' : 'left';
    showArrow.value = true;
    
    setTimeout(() => {
      propsData.value = data;
      console.log(data);
      selected.value = true;
      selectedSection.value = section;
      showArrow.value = false;
    }, 500);
  };
  
  const unselectSection = () => {
    selectedSection.value = '';
    selected.value = false;
  };
  
  onMounted(() => {
    propsData.value = filteredDrivingData;
    selected.value = true;
  });
  
  console.log("filteredParkingData", filteredParkingData);
  console.log("propsData", propsData.value);
  </script> -->




<!--   
  <style scoped>

  .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  
  .arrow-right {
    animation: moveRightArrow 0.5s forwards;
  }
  
  .arrow-left {
    animation: moveLeftArrow 0.5s forwards;
  }
  
  @keyframes moveRightArrow {
    0% {
      opacity: 0;
      transform: translate(-50%, -50%) translateX(-20px);
    }
    50% {
      opacity: 1;
      transform: translate(-50%, -50%) translateX(0);
    }
    100% {
      opacity: 3;
      transform: translate(-50%, -50%) translateX(10px);
    }
  }
  
  @keyframes moveLeftArrow {
    0% {
      opacity: 0;
      transform: translate(-50%, -50%) translateX(20px);
    }
    50% {
      opacity: 1;
      transform: translate(-50%, -50%) translateX(0);
    }
    100% {
      opacity: 2;
      transform: translate(-50%, -50%) translateX(-20px);
    }
  }



  </style> -->

<!-- <template>
  <main class="bg-white mt-10 py-5 3xl:px-[10px] 3xl:mt-5 rounded-lg xl:w-[1200px] 1xl:w-[1280px] 2xl:w-[1460px] 3xl:w-[1830px] xl:ml-[-60px] 1xl:ml-[-100px] 2xl:ml-[-190px] 3xl:ml-[-60px] 3xl:h-[900px]">
    
    <div class="flex">
      <aside class="container pt-10 rounded-lg ml-5 1xl:h-[500px] 2xl:h-[550px] pb-10 1xl:w-[680px] 2xl:w-[800px] 3xl:w-[1000px] 3xl:h-[740px]" style="background-color:#EFF2EF;">
        
        <main class="flex justify-evenly bg-red-00 mr-5">
          <div class="relative bg-white cursor-pointer 1xl:w-[280px] border-2 border-blue-500 2xl:w-[300px] 3xl:w-[380px] 3xl:h-[600px]" 
               :class="['bg-white cursor-pointer', { 'border-4 border-red-500 rounded-lg': selectedSection === 'driving' }]"
               @click="sendData($event, filteredDrivingData, 'driving')"
               @dblclick="unselectSection">
            <div v-if="showArrow && selectedSection === 'driving'" class="absolute top-0 left-1/2 transform -translate-x-1/2 text-4xl text-red-500 arrow-animation">
              ↓
            </div>
          </div>
          
          <div class="relative bg-white ml-5 cursor-pointer border-2 border-blue-500 1xl:w-[280px] 2xl:w-[300px] 3xl:w-[380px] 3xl:h-[600px] 3xl:ml-[40px]"
               :class="['bg-white ml-5 cursor-pointer', { 'border-4 border-red-500 rounded-lg': selectedSection === 'parking' }]" 
               @click="sendData($event, filteredParkingData, 'parking')"
               @dblclick="unselectSection">
            <div v-if="showArrow && selectedSection === 'parking'" class="absolute top-0 left-1/2 transform -translate-x-1/2 text-4xl text-red-500 arrow-animation">
              ↓
            </div>
          </div>
        </main>
      </aside>
      
    </div>
  </main>
</template> -->

<script setup>
import { ref, onMounted } from 'vue';
import Servicelocation from "../mco/service-location.vue";
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
  
  const hostnames = ["SOC0", "SOC1", "ZONAL"];
  
  let propsData = ref(filteredDrivingData);
  
  const selected = ref(false);

const showArrow = ref(false);
const selectedSection = ref('');

const sendData = (event, data, section) => {
  console.log("click");
  showArrow.value = true;
  selectedSection.value = section;
  
  setTimeout(() => {
    propsData.value = data;
    console.log(data);
    selected.value = true;
    showArrow.value = false;
  }, 2000);
};

const unselectSection = () => {
  selectedSection.value = '';
  selected.value = false;
  showArrow.value = false;
};

onMounted(() => {
    propsData.value = filteredDrivingData;
    selected.value = true;
  });
  
  console.log("filteredParkingData", filteredParkingData);
  console.log("propsData", propsData.value);
// ... (rest of the script)
</script>

<style scoped>


.arrow-animation {

  animation: fadeInOut 4s forwards;
  animation: bounceAnimation 4s infinite; 
}

@keyframes bounceAnimation {
  0%, 100% {
    transform: translateY(0); 
  }
  50% {
    transform: translateY(-20px); 
  }
}

@keyframes fadeInOut {
  0% { opacity: 0; transform: translate(-50%, -20px); }
  20% { opacity: 1; transform: translate(-50%, 0); }
  80% { opacity: 1; transform: translate(-50%, 0); }
  100% { opacity: 0; transform: translate(-50%, 0); }
}





  /* Fade transition effect */
  .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  
  /* Arrow Animation */
  .arrow-right {
    animation: moveRightArrow 0.5s forwards;
  }
  
  .arrow-left {
    animation: moveLeftArrow 0.5s forwards;
  }
  
  @keyframes moveRightArrow {
    0% {
      opacity: 0;
      transform: translate(-50%, -50%) translateX(-20px);
    }
    50% {
      opacity: 1;
      transform: translate(-50%, -50%) translateX(0);
    }
    100% {
      opacity: 3;
      transform: translate(-50%, -50%) translateX(10px);
    }
  }
  
  @keyframes moveLeftArrow {
    0% {
      opacity: 0;
      transform: translate(-50%, -50%) translateX(20px);
    }
    50% {
      opacity: 1;
      transform: translate(-50%, -50%) translateX(0);
    }
    100% {
      opacity: 2;
      transform: translate(-50%, -50%) translateX(-20px);
    }
  }

</style>
