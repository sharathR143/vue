


<template>
  <main class="bg-white mt-10  py-5  3xl:px-[10px] 3xl:mt-5 rounded-lg  xl:w-[1200px] 1xl:w-[1280px] 2xl:w-[1460px] 3xl:w-[1830px] xl:ml-[-60px] 1xl:ml-[-100px] 2xl:ml-[-190px] 3xl:ml-[-60px]  3xl:h-[900px]">
    <div>
      <h1 class="font-bold  uppercase  mb-[10px]  pl-5 text-[#992121]  text-[20px] 1xl:text-[17px] 3xl:text-[23px]">PICCOLO Design studio</h1>
    </div>

    
    <div class="flex">
      <aside  class="container pt-10  rounded-lg  ml-5  1xl:h-[500px] 2xl:h-[550px] pb-10  1xl:w-[680px] 2xl:w-[800px]  3xl:w-[1000px] 3xl:h-[740px]  " style="background-color:#EFF2EF;">
        <div class="pr-2 mt-[0px] ml-4  bg-red-00 relative left-[-10px] top-[-30px]  w-[100px] h-[30px] ">

          <div class="flex  bg-red-00 w-[250px] justify-between  ">
            <v-btn :icon="showPiccoloScenario ? 'mdi-close' : 'mdi-plus'" size="small" color="primary" @click="togglePiccoloScenario"  class="cursor-pointer "></v-btn>
            <div v-if="showPiccoloScenario" class="mr-2 mt-2 text-[20px] text-[#992121] font-bold">Scenario Creator</div>
          </div>
          
        </div>

      <header v-if="!showPiccoloScenario" >
        <main class="flex  justify-evenly  bg-red-00 mr-5 ">
           <div class=" bg-white cursor-pointer 1xl:w-[280px] border-2 border-blue-500 2xl:w-[300px]  3xl:w-[380px] 3xl:h-[600px] " 
           :class="['bg-white cursor-pointer', { 'border-4 border-red-500  rounded-lg': selectedSection === 'driving' }]"
         
            @click="sendData($event, filteredDrivingData,'driving')"
            @dblclick="unselectSection()">

            <div v-if="showArrow && selectedSection === 'driving'" class="absolute top-[100px] 3xl:top-[110px] left-[190px]  2xl:left-[220px]  3xl:left-[310px] transform -translate-x-1/2 text-4xl text-red-500 arrow-animation">                
                <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 1080 1080" width="80" height="80" preserveAspectRatio="xMidYMid meet" style="width: 100%; height: 100%; transform: translate3d(0px, 0px, 0px)   rotate(90deg); content-visibility: visible;"><defs><clipPath id="__lottie_element_27881"><rect width="1080" height="1080" x="0" y="0"></rect></clipPath></defs><g clip-path="url(#__lottie_element_27881)"><g transform="matrix(3.190000057220459,0,0,3.190000057220459,424.0982666015625,338.81280517578125)" opacity="1" style="display: block;"><g opacity="1" transform="matrix(1,0,0,1,50.72800064086914,64.3219985961914)"><path fill="rgb(255,94,0)" fill-opacity="1" d=" M46.05500030517578,5.840000152587891 C50.479000091552734,2.628000020980835 50.479000091552734,-2.628999948501587 46.05500030517578,-5.841000080108643 C46.05500030517578,-5.841000080108643 -44.599998474121094,-60.858001708984375 -44.599998474121094,-60.858001708984375 C-49.02399826049805,-64.07099914550781 -50.47800064086914,-61.874000549316406 -47.83100128173828,-55.97700119018555 C-47.83100128173828,-55.97700119018555 -16.658000946044922,0 -16.658000946044922,0 C-16.658000946044922,0 -47.83100128173828,55.97700119018555 -47.83100128173828,55.97700119018555 C-50.47800064086914,61.874000549316406 -49.02399826049805,64.07099914550781 -44.599998474121094,60.85900115966797 C-44.599998474121094,60.85900115966797 46.05500030517578,5.840000152587891 46.05500030517578,5.840000152587891z"></path></g><g opacity="1" transform="matrix(1,0,0,1,50.8380012512207,95.49099731445312)"><path fill="rgb(206,76,0)" fill-opacity="1" d=" M-16.767000198364258,-31.16900062561035 C-16.767000198364258,-31.16900062561035 -47.941001892089844,24.808000564575195 -47.941001892089844,24.808000564575195 C-50.5880012512207,30.704999923706055 -49.13399887084961,32.902000427246094 -44.709999084472656,29.690000534057617 C-44.709999084472656,29.690000534057617 45.94499969482422,-25.32900047302246 45.94499969482422,-25.32900047302246 C48.15700149536133,-26.934999465942383 49.26300048828125,-29.052000045776367 49.26300048828125,-31.16900062561035 C49.26300048828125,-31.16900062561035 -16.767000198364258,-31.16900062561035 -16.767000198364258,-31.16900062561035z"></path></g></g><g transform="matrix(3.190000057220459,0,0,3.190000057220459,264.09820556640625,338.81280517578125)" opacity="1" style="display: block;"><g opacity="1" transform="matrix(1,0,0,1,50.72800064086914,64.3219985961914)"><path fill="rgb(255,94,0)" fill-opacity="1" d=" M46.05500030517578,5.840000152587891 C50.479000091552734,2.628000020980835 50.479000091552734,-2.628999948501587 46.05500030517578,-5.841000080108643 C46.05500030517578,-5.841000080108643 -44.599998474121094,-60.858001708984375 -44.599998474121094,-60.858001708984375 C-49.02399826049805,-64.07099914550781 -50.47800064086914,-61.874000549316406 -47.83100128173828,-55.97700119018555 C-47.83100128173828,-55.97700119018555 -16.658000946044922,0 -16.658000946044922,0 C-16.658000946044922,0 -47.83100128173828,55.97700119018555 -47.83100128173828,55.97700119018555 C-50.47800064086914,61.874000549316406 -49.02399826049805,64.07099914550781 -44.599998474121094,60.85900115966797 C-44.599998474121094,60.85900115966797 46.05500030517578,5.840000152587891 46.05500030517578,5.840000152587891z"></path></g><g opacity="1" transform="matrix(1,0,0,1,50.8380012512207,95.49099731445312)"><path fill="rgb(206,76,0)" fill-opacity="1" d=" M-16.767000198364258,-31.16900062561035 C-16.767000198364258,-31.16900062561035 -47.941001892089844,24.808000564575195 -47.941001892089844,24.808000564575195 C-50.5880012512207,30.704999923706055 -49.13399887084961,32.902000427246094 -44.709999084472656,29.690000534057617 C-44.709999084472656,29.690000534057617 45.94499969482422,-25.32900047302246 45.94499969482422,-25.32900047302246 C48.15700149536133,-26.934999465942383 49.26300048828125,-29.052000045776367 49.26300048828125,-31.16900062561035 C49.26300048828125,-31.16900062561035 -16.767000198364258,-31.16900062561035 -16.767000198364258,-31.16900062561035z"></path></g></g></g></svg>
          </div>

            <div class="mb-5 bg-gray-00">
              <img src="/img/car.png" alt="Driving image" class="w-[260px] mx-2 mt-3  2xl:w-[280px] 3xl:w-[360px] 3xl:h-[250px]  rounded-lg h-[150px] 2xl:h-[200px]">  
              <p class="flex justify-end mr-3  font-bold">Driving</p>
            </div>
            

            <aside class="xl:mt-6 1xl:mt-5 2xl:mt-1  3xl:mt-[50px]   3xl:ml-[px]">
             <div class=" bg-red-00  ml-[80px] xl:ml-[100px] 1xl:ml-[60px]  2xl:ml-[73px] 3xl:ml-[100px] mb-1">
                  <div class="flex justify-center items-center h-[20px]  1xl:h-[30px]  bg-blue-300  xl:w-[70px]  1xl:w-[60px]  2xl:w-[68px] 3xl:w-[80px] mx-10 px-7 py-3   3xl:py-5  3xl:h-[37px]">
                       <p class="">rdv</p>
                  </div>
             </div>
             <div class=" bg-red-00  ml-[80px] xl:ml-[100px]  1xl:ml-[60px] 2xl:ml-[73px] 3xl:ml-[100px] mb-1">
                 <div class="flex  justify-center items-center h-[20px]  1xl:h-[30px]  bg-blue-300   xl:w-[70px] 1xl:w-[60px] 2xl:w-[68px]  3xl:w-[80px]  mx-10 px-7 py-3  3xl:py-5 3xl:h-[37px] ml-">
                  <p class="">mavd</p>
                  </div>
              </div>
              <div class="bg-red-00  ml-[80px] xl:ml-[100px] 1xl:ml-[60px]  2xl:ml-[73px] 3xl:ml-[100px] mb-1">
                  <div class="flex justify-center items-center  h-[20px]  1xl:h-[30px]  bg-blue-300  xl:w-[70px] 1xl:w-[60px] 2xl:w-[68px] 3xl:w-[80px]  mx-10 px-7 py-3  3xl:py-5  3xl:h-[37px] ml-">
                      <p class="">frism</p>
                  </div>
              </div>
              <div class=" bg-red-00  ml-[80px] xl:ml-[100px] 1xl:ml-[60px]  2xl:ml-[73px] 3xl:ml-[100px]">
                  <div class="flex justify-center items-center  h-[20px]  1xl:h-[30px]  bg-blue-300   xl:w-[70px] 1xl:w-[60px] 2xl:w-[68px]  3xl:w-[80px]  mx-10 px-7 py-3   3xl:py-5 3xl:h-[37px]  ml-">
                       <p class="">blis</p>
                      </div>
                  </div>
              <div class="flex h-[60px] bg-red-00 w-[100px] ml-[80px] mt-2 1xl:mt-5 xl:ml-[10px] 1xl:ml-[22px] 2xl:ml-[25px] 3xl:ml-[40px] ">
                  <div class="flex justify-center items-center">

                      <div class="text-center border-dashed border-2 border-sky-500   w-[120px]  xl:w-[70px] 1xl:w-[60px] 2xl:w-[70px] 2xl:px-1 1xl:px-1  1xl:py-1 2xl:py-2  mr-4 3xl:w-[80px]   "  style="background-color:#FFFFFF" >
                          <p class="">SOC0</p>
                      </div>

                      <div  class="text-center border-dashed border-2 border-sky-500  w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[70px]  2xl:px-1 1xl:px-1  1xl:py-1 2xl:py-2 mr-4   3xl:w-[80px] "  style="background-color:#FFFFFF">
                          <p class=" ">SOC1</p>
                      </div>

                      <div  class="text-center border-dashed border-2 border-sky-500 bg-gray-300 w-[120px] xl:w-[60px] 1xl:w-[60px] 2xl:w-[70px]  1xl:px-1  1xl:py-1 2xl:px-1  2xl:py-2 mr-4    3xl:w-[80px] ">
                          <p class="">ZONAL</p>
                      </div>
                  </div>
              </div>
             </aside>
          </div> 




        

        
         <div class="bg-white ml-5  cursor-pointer border-2 border-blue-500 1xl:w-[280px]  2xl:w-[300px]  3xl:w-[380px] 3xl:h-[600px]  3xl:ml-[40px]"
         :class="['bg-white ml-5 cursor-pointer', { 'border-4 border-red-500  rounded-lg ': selectedSection === 'parking' }]" 
          @click="sendData($event, filteredParkingData,'parking')" @dblclick="unselectSection()">

          <div v-if="showArrow && selectedSection === 'parking'" class="absolute   top-[100px] 3xl:top-[110px] 1xl:left-[520px] 2xl:left-[590px] 3xl:left-[770px] transform -translate-x-1/2 text-4xl text-red-500 arrow-animation ">
            <!-- <img src="/img/Animation-arrow.gif" alt="Driving image" class="mx-2 mt-3 w-[100px] h-[100px]   2xl:w-[100px] 2xl:h-[100px] 3xl:w-[100px] 3xl:h-[100px]  rounded-lg  ">   -->
         
           <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 1080 1080" width="80" height="80" preserveAspectRatio="xMidYMid meet" style="width: 100%; height: 100%; transform: translate3d(0px, 0px, 0px)   rotate(90deg); content-visibility: visible;"><defs><clipPath id="__lottie_element_27881"><rect width="1080" height="1080" x="0" y="0"></rect></clipPath></defs><g clip-path="url(#__lottie_element_27881)"><g transform="matrix(3.190000057220459,0,0,3.190000057220459,424.0982666015625,338.81280517578125)" opacity="1" style="display: block;"><g opacity="1" transform="matrix(1,0,0,1,50.72800064086914,64.3219985961914)"><path fill="rgb(255,94,0)" fill-opacity="1" d=" M46.05500030517578,5.840000152587891 C50.479000091552734,2.628000020980835 50.479000091552734,-2.628999948501587 46.05500030517578,-5.841000080108643 C46.05500030517578,-5.841000080108643 -44.599998474121094,-60.858001708984375 -44.599998474121094,-60.858001708984375 C-49.02399826049805,-64.07099914550781 -50.47800064086914,-61.874000549316406 -47.83100128173828,-55.97700119018555 C-47.83100128173828,-55.97700119018555 -16.658000946044922,0 -16.658000946044922,0 C-16.658000946044922,0 -47.83100128173828,55.97700119018555 -47.83100128173828,55.97700119018555 C-50.47800064086914,61.874000549316406 -49.02399826049805,64.07099914550781 -44.599998474121094,60.85900115966797 C-44.599998474121094,60.85900115966797 46.05500030517578,5.840000152587891 46.05500030517578,5.840000152587891z"></path></g><g opacity="1" transform="matrix(1,0,0,1,50.8380012512207,95.49099731445312)"><path fill="rgb(206,76,0)" fill-opacity="1" d=" M-16.767000198364258,-31.16900062561035 C-16.767000198364258,-31.16900062561035 -47.941001892089844,24.808000564575195 -47.941001892089844,24.808000564575195 C-50.5880012512207,30.704999923706055 -49.13399887084961,32.902000427246094 -44.709999084472656,29.690000534057617 C-44.709999084472656,29.690000534057617 45.94499969482422,-25.32900047302246 45.94499969482422,-25.32900047302246 C48.15700149536133,-26.934999465942383 49.26300048828125,-29.052000045776367 49.26300048828125,-31.16900062561035 C49.26300048828125,-31.16900062561035 -16.767000198364258,-31.16900062561035 -16.767000198364258,-31.16900062561035z"></path></g></g><g transform="matrix(3.190000057220459,0,0,3.190000057220459,264.09820556640625,338.81280517578125)" opacity="1" style="display: block;"><g opacity="1" transform="matrix(1,0,0,1,50.72800064086914,64.3219985961914)"><path fill="rgb(255,94,0)" fill-opacity="1" d=" M46.05500030517578,5.840000152587891 C50.479000091552734,2.628000020980835 50.479000091552734,-2.628999948501587 46.05500030517578,-5.841000080108643 C46.05500030517578,-5.841000080108643 -44.599998474121094,-60.858001708984375 -44.599998474121094,-60.858001708984375 C-49.02399826049805,-64.07099914550781 -50.47800064086914,-61.874000549316406 -47.83100128173828,-55.97700119018555 C-47.83100128173828,-55.97700119018555 -16.658000946044922,0 -16.658000946044922,0 C-16.658000946044922,0 -47.83100128173828,55.97700119018555 -47.83100128173828,55.97700119018555 C-50.47800064086914,61.874000549316406 -49.02399826049805,64.07099914550781 -44.599998474121094,60.85900115966797 C-44.599998474121094,60.85900115966797 46.05500030517578,5.840000152587891 46.05500030517578,5.840000152587891z"></path></g><g opacity="1" transform="matrix(1,0,0,1,50.8380012512207,95.49099731445312)"><path fill="rgb(206,76,0)" fill-opacity="1" d=" M-16.767000198364258,-31.16900062561035 C-16.767000198364258,-31.16900062561035 -47.941001892089844,24.808000564575195 -47.941001892089844,24.808000564575195 C-50.5880012512207,30.704999923706055 -49.13399887084961,32.902000427246094 -44.709999084472656,29.690000534057617 C-44.709999084472656,29.690000534057617 45.94499969482422,-25.32900047302246 45.94499969482422,-25.32900047302246 C48.15700149536133,-26.934999465942383 49.26300048828125,-29.052000045776367 49.26300048828125,-31.16900062561035 C49.26300048828125,-31.16900062561035 -16.767000198364258,-31.16900062561035 -16.767000198364258,-31.16900062561035z"></path></g></g></g></svg>

          </div>

          <div class="mb-5 bg-green-00">
            <img src="/img/car1.png" alt="parking image" class="w-[260px] mx-2 mt-3  rounded-lg  2xl:w-[280px] h-[150px] 2xl:h-[200px]   3xl:w-[360px] 3xl:h-[250px]">  
            <p class="flex justify-end mr-3 font-bold">Parking</p>
          </div>


         <aside class="mt-16 1xl:pt-[38px] 2xl:pt-[40px]  3xl:pt-[105px]  3xl:ml-5">
          <div class="flex  bg-red-00  w-[1200px] h-[40px] bg-red-00  ">

               <div class="flex justify-center items-center bg-blue-300 w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[68px] 3xl:w-[80px]  h-[20px]  1xl:h-[40px]  2xl:h-[36px] 3xl::h-[40px] ml-[80px] xl:ml-[40px] 1xl:ml-[22px] 2xl:ml-[26px] 3xl:ml-[30px]  ">
                    <p class=" ">blis</p>
               </div>
               <div  class="flex justify-center items-center  bg-blue-300 w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[68px] 3xl:w-[80px] h-[20px]  1xl:h-[40px] 2xl:h-[36px] 3xl::h-[40px] ml-[80px] xl:ml-[40px]  1xl:ml-[90px] 2xl:ml-[105px]  3xl:ml-[115px]  ">
                    <p class="">frism</p>
               </div>
           
           </div>
           
            <div class="flex  h-[60px] bg-red-00 w-[100px] ml-[80px]  mt-3  1xl:mt-5  xl:ml-[20px] 1xl:ml-[22px] 2xl:ml-[25px] 3xl:ml-[30px]">
               <div class="flex justify-center items-center">

                   <div class="text-center border-dashed border-2 border-sky-500   w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[70px]  3xl:w-[80px] 1xl:px-1  1xl:py-1 2xl:px-1  2xl:py-2 mr-4  "  style="background-color:#FFFFFF" >
                       <p class="">SOC0</p>
                   </div>

                   <div  class="text-center border-dashed border-2 border-sky-500  w-[120px] xl:w-[70px] 1xl:w-[60px] 2xl:w-[70px] 3xl:w-[80px] 1xl:px-1  1xl:py-1 2xl:px-1  2xl:py-2  mr-4 "  style="background-color:#FFFFFF">
                       <p class="">SOC1</p>
                   </div>

                   <div  class="text-center border-dashed border-2 border-sky-500 bg-gray-300 w-[120px] xl:w-[80px] 1xl:w-[60px] 2xl:w-[70px]  3xl:w-[80px] 1xl:px-1  1xl:py-1 2xl:px-1  2xl:py-2   mr-4  ">
                       <p class="">ZONAL</p>
                   </div>
               </div>
           </div>
   </aside>
       
        </div>
      </main>

      </header>

      <PiccoloScenario v-else @close="showPiccoloScenario = false" />


    </aside>
     <aside>
      <Servicelocation :drivingjson="propsData" :selected="selected" :selectedName="selectedSection" class="relative top-[-420px] left-[25px] xl:top-[-10px] xl:left-[30px]  1xl:top-[0px] 1xl:left-[10px]  2xl:top-[0px] 2xl:left-[20px]  3xl:left-[70px]" />
    </aside> 

  </div>
</main> 
</template>


<script setup>
import { ref, onMounted } from 'vue';
import PiccoloScenario from './PiccoloScenario.vue';
import { useRouter } from 'vue-router';
import Servicelocation from "../mco/service-location.vue";
import driving from "../../data/container-Driving.json";
import parking from "../../data/container-parking.json";

const router=useRouter()

const showPiccoloScenario = ref(false);
const navigateToNewcomponent=()=>{
  router.push("/newcomponent")
}

const togglePiccoloScenario = () => {
  showPiccoloScenario.value = !showPiccoloScenario.value;
};


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
</script>

<style scoped>
.v-icon {
font-size: 25px; /* Increase icon size */
}


.arrow-animation {

animation: fadeInOut 4s forwards;
animation: bounceAnimation 3s infinite; 
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
