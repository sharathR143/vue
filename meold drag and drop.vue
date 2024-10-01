

<template>
<main class="bg-white mt-2  py-5  3xl:px-[10px] 3xl:mt-5 rounded-lg  xl:w-[1200px] 1xl:w-[1280px] 2xl:w-[1460px] 3xl:w-[1830px] xl:ml-[-60px] 1xl:ml-[-100px] 2xl:ml-[-190px] 3xl:ml-[-60px]">
  <div>
    <h1 class="font-bold  uppercase  mb-[10px]  pl-5 text-[#992121]  text-[20px] 1xl:text-[17px] 3xl:text-[23px] ">PICCOLO Design studio</h1>
  </div>

  <aside class="container  rounded-lg  ml-5 h-[350px] 3xl:h-[420px] xl:w-[1160px] 1xl:w-[1250px] 2xl:w-[1430px] 3xl:w-[1772px]" style="background-color:#EFF2EF;">
              <!-- condition items -->
    <header>
      <div class="pt-3 ml-[10px] my-5 rounded-lg  bg-slate-00  shadow-xl  xl:w-[300px]  1xl:w-[340px] 2xl:w-[380px] 3xl:w-[450px]  h-[340px] xl:h-[240px] 1xl:h-[240px] 3xl:h-[300px]" style="background-color:#FFFFFF">
        <h3 class="pb-5 font-bold  text-gray-700 text-center  text-[18px] xl:text-[14px] 1xl:text-[14px] 3xl:text-[20px] ">Condition Items</h3>
        <div class="flex flex-wrap overflow-auto bg-red-00  xl:pl-[20px] 1xl:pl-[30px] h-[270px] xl:h-[170px]  1xl:h-[180px] 3xl:h-[230px] ">
          <div v-for="(name, index) in conditions" :key="index"   class="draggable"  draggable="true"  @dragstart="onDragStart(name)">
            <button class="bg-blue-300  rounded-full  px-2  py-2  1xl:mb-1  2xl:mb-0  3xl:mb-2  cursor-grab  font-sans font-medium  text-gray-700  xl:text-[11px] 1xl:text-[11px]  2xl:text-[13px]  3xl:text-[15px]  xl:w-[110px] 1xl:w-[120px] 2xl:w-[140px] 3xl:w-[170px] 3xl:h-[40px]  
            transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5  bg-gradient-to-r from-blue-400 to-blue-400  hover:from-blue-400 hover:to-blue-500">{{ name }}</button>
          </div>
        </div>
      </div>


             <!-- create and cancel btn -->
      <div class="mt-2 mb-3  xl:ml-[8px] 1xl:ml-[10px] 3xl:pt-[15px]">
        <button class="px-2 py-2  mx-[10px] rounded-md w-[100px]  text-sm   text-white   bg-gradient-to-r from-green-400 to-green-600  hover:from-green-500 hover:to-green-700  transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5  shadow-green-500/50 " @click="createTemplate">Create</button>
        <button class="px-2 py-2  mx-[10px] rounded-md w-[100px]  text-sm   text-white   bg-gradient-to-r from-red-400 to-red-600  hover:from-red-500 hover:to-red-700  transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5  shadow-red-500/50 " @click="cancelTemplate"  :disabled="!isCancelEnabled"   :class="{ 'opacity-50 cursor-not-allowed': !isCancelEnabled}">Cancel</button>
      </div>
    </header>

              <!-- dropped condition -->    
    <div class="overflow-auto mx-5 border-dashed border-2 border-blue-500  rounded-lg   w-[300px]  h-[300px]  xl:h-[170px] 1xl:h-[180px] 2xl:h-[180px] 3xl:h-[215px] xl:mt-[60px] 1xl:mt-[60px] 2xl:mt-[50px]  3xl:mt-[70px] pt-[40px] xl:pt-[10px] 1xl:pt-[10px] 3xl:pt-[30px]" @dragover.prevent @drop="onDropConditions">
      <h3 class=" text-center font-sans font-medium  text-gray-500">(Conditions)</h3>
      <div v-if="droppedConditions.length > 0">
        <div v-for="(name, index) in droppedConditions" :key="index" class="dropped-item  pl-[40px]  mt-[5px]">
          <button class="bg-blue-300 flex justify-evenly cursor-default  rounded-full  px-2 py-2 my-2  w-[160px] xl:w-[140px] 1xl:w-[136px] 2xl:w-[160px] 3xl:w-[180px] xl:ml-[5px] 1xl:ml-[10px] 2xl:ml-[20px] 3xl:ml-[20px]  xl:text-[11px]   1xl:text-[11px]  2xl:text-[13px]  3xl:text-[15px]  transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5  bg-gradient-to-r from-blue-400 to-blue-400  hover:from-blue-400 hover:to-blue-500  ">
                 <span class=" px-2 text-center  font-sans font-medium text-gray-700 ">{{ name }}</span>
                 <span class="remove-icon" @click="removeCondition(index)"><v-icon color="primary"> mdi-close-circle</v-icon></span>
          </button>
        </div>
      </div>

      <div v-else>
        <span class="relative  top-[70px] left-[80px]  xl:top-[50px]  xl:left-[70px]  1xl:top-[50px]  1xl:left-[80px]  2xl:left-[100px]  3xl:left-[110px]  text-slate-500 hover:text-blue-600"><button class="animate-bounce  text-center cursor-default"> Drop Here</button></span>
      </div>
    </div>


             <!-- plus icons -->    
    <div class="pr-5 mt-[150px] 1xl:mt-[130px] 3xl:mt-[150px] ">
      <v-icon color="primary">mdi-plus</v-icon>
    </div>


           <!-- dropped Actions -->    
    <div class="border-dashed  border-2 border-red-500  rounded-lg  mr-5  pt-[40px]  xl:pt-[10px]  1xl:pt-[10px]  3xl:pt-[30px]  xl:mt-[60px]  1xl:mt-[60px]  2xl:mt-[50px]  3xl:mt-[70px]  w-[300px]  2xl:w-[280px] 3xl:w-[300px]  h-[300px]  xl:h-[170px]  1xl:h-[180px]  2xl:h-[180px]  3xl:h-[215px]" @dragover.prevent @drop="onDropActions">
      <h3 class=" text-center font-sans font-medium  text-gray-500">(Actions)</h3>
      <div v-if="droppedAction">
        <div v-if="droppedAction" class="dropped-item flex flex-wrap pt-[40px] xl:pt-[10px] 1xl:pt-[20px] ">
          <button class="cursor-default  rounded-full  w-[120px] xl:w-[80px]  1xl:w-[90px]  2xl:w-[96px]  3xl:w-[120px]  h-[120px]  xl:h-[80px]  1xl:h-[90px]  2xl:h-[96px]  3xl:h-[120px]   ml-[60px]  xl:ml-[70px]  1xl:ml-[80px]  2xl:ml-[90px] 3xl:ml-[90px]   xl:text-[11px]   1xl:text-[11px]  2xl:text-[13px]  3xl:text-[15px] transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5  bg-gradient-to-r from-red-300 to-red-300  hover:from-red-300 hover:to-red-400  ">
            <div class="remove-icon mb-2 mr-2 " @click="removeAction">
              <v-icon > mdi-close-circle</v-icon>
            </div>

            <div class=" text-center  cursor-default  font-sans font-medium text-gray-700 px-2 ">
              {{ droppedAction }}
            </div>
          </button>
        </div>
      </div>

      <div v-else>
        <span class="relative  top-[70px] left-[80px] xl:top-[50px] xl:left-[80px] 2xl:left-[100px] 3xl:left-[110px]   text-slate-500 hover:text-red-600"><button class="animate-bounce  cursor-default"> Drop Here</button></span>
      </div>
    </div>


              <!-- Actions Items -->    
    <div class="rounded-lg pt-3  mr-2  my-5  3xl:pt-2  ml-[10px]  w-[380px]  3xl:w-[450px]  h-[340px]  xl:h-[240px]  1xl:h-[240px]  3xl:h-[310px] shadow-xl "  style="background-color:#FFFFFF">
      <h3 class="font-bold text-gray-700  text-center text-[18px]  xl:text-[14px] 1xl:text-[14px] 3xl:text-[20px]  pb-[20px] 1xl:pb-[20px] 2xl:pb-[20px] 3xl:pb-[20px]  ">Action Items</h3>
      <div class="overflow-auto flex flex-wrap  xl:pl-[10px] 1xl:pl-[10px] 2xl:pl-[8px]  3xl:pl-[40px] h-[270px] xl:h-[170px] 1xl:h-[180px] 3xl:h-[250px] ">
        <div  v-for="(action, index) in actions" :key="index"  class="draggable"  draggable="true"   @dragstart="onDragStart(action)">
          <button class="2xl:mr-5 px-2 py-2  cursor-grab font-sans font-medium text-gray-700 xl:text-[11px]   1xl:text-[11px]  2xl:text-[13px]  3xl:text-[15px]  rounded-full  xl:w-[70px]  1xl:w-[70px] 2xl:w-[80px] 3xl:w-[100px] xl:h-[70px] 1xl:h-[70px]  2xl:h-[80px]  3xl:h-[100px]    xl:mb-2 1xl:mb-3 2xl:mb-0 3xl:mb-3   transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5  bg-gradient-to-r from-red-300 to-red-300   hover:from-red-300 hover:to-red-400">
            {{ action }}
         </button>
        </div>
      </div>
    </div>
  </aside>


            <!-- Design sections -->    
  <footer class="flex">
      <aside class="ml-4 3xl:ml-0 xl:mt-[18px] 1xl:mt-[28px] 2xl:mt-[20px] rounded-lg  xl:w-[580px] 1xl:w-[630px] 2xl:w-[750px] 3xl:w-[850px]  xl:h-[390px] 1xl:h-[430px] " style="background-color:#EFF2EF;">
        <div class="mt-[0px]">
          <h3 class="py-[20px] ml-[20px] text-[#992121] uppercase   font-bold  text-[16px]  1xl:text-[17px]  3xl:text-[20px]">Designs</h3>
          <div  class=" flex flex-wrap ml-4 mt-2  bg-red-800 pl-[10px] border-dashed rounded-lg  border-2 border-gray-300  xl:w-[550px] 1xl:w-[575px]   2xl:w-[720px]   3xl:w-[800px]  xl:h-[250px] 1xl:h-[300px] " style="background-color:#FFFFFF">
            <!-- Save,Restore,Delete all buttons -->
            <div class="flex justify-end static mb-1  mt-1  h-[34px]  w-[1200px] 3xl:w-[1450px]">
              <button class="px-2  1xl:py-2  mx-[5px]  rounded-md  text-sm  xl:text-[11px]  1xl:text-sm  xl:w-[40px]  1xl:w-[50px]   text-white bg-gradient-to-r from-purple-400 to-purple-600  hover:from-purple-500 hover:to-purple-700   transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5    shadow-gray-500/50 " @click="saveTemplates">Save</button>
              <button class="px-2  py-2  mx-[5px]  rounded-md  w-[60px]  text-sm text-white bg-gradient-to-r from-indigo-400 to-indigo-600  hover:from-indigo-500 hover:to-indigo-700   transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5    shadow-gray-500/50 " @click="restoreTemplates">Restore</button>
              <button class="px-2  py-2  mx-[5px]  rounded-md  w-[35px]  text-sm text-white bg-gradient-to-r from-yellow-400 to-yellow-600  hover:from-yellow-500 hover:to-yellow-700   transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5    shadow-gray-500/50 " @click="DeleteAllTemplates"> 
                <v-tooltip activator="parent" location="top"  class="font-semibold   "> Remove All Card !</v-tooltip>   
                <img :src="`/img/broom.png`" alt="icon" style="height: 30px; width: 18px; margin-top: -6px;">
              </button>
            </div>


                          <!-- card section --> 
            <aside class=" overflow-auto  flex  flex-wrap  xl:h-[200px]  1xl:h-[242px]" v-if="generatedTemplates.length>0">
              <div  v-for="(template, index) in generatedTemplates" :key="index" 
              class="overflow-auto cursor-pointer px-2 pt-1  mb-3  bg-white  text-center  rounded-lg  xl:w-[160px]  1xl:w-[170px]  2xl:w-[220px]  3xl:w-[240px]    xl:h-[200px]   1xl:h-[230px]   xl:ml-[10px]  1xl:ml-[10px]   3xl:mx-[8px] "
              :class="{ selected: selectedCardIndex === index }"
              @click="selectCard(index)"
              >

              <div class="overflow-auto  overflow-y-auto  bg-gray-200   rounded-lg  mx-auto  h-[190px]  1xl:h-[220px]  [&::-webkit-scrollbar]:w-2  [&::-webkit-scrollbar-track]:rounded-full   [&::-webkit-scrollbar-track]:bg-gray-100  [&::-webkit-scrollbar-thumb]:rounded-full  [&::-webkit-scrollbar-thumb]:bg-gray-400/50  dark:[&::-webkit-scrollbar-track]:bg-neutral-700   dark:[&::-webkit-scrollbar-thumb]:bg-neutral-500 ">
                <header>
                  <div class="mt-5 font-weight-black  xl:text-[12px] 1xl:text-[13px] 2xl:text-[14px] 3xl:text-[17px]  text-gray-500 ">Conditions:</div>
                  <div v-for="(condition, index) in template.conditions" :key="index" class="flex  justify-center items-center mt-2 ">
                    <div class="flex justify-center items-center bg-blue-400 px-2 py-1 rounded-full mb-2 font-sans font-medium  text-gray-700  text-[11px]  1xl:text-[11px]  2xl:text-[13px]  3xl:text-[15px]   xl:w-[100px] xl:h-[30px]  1xl:w-[120px] 1xl:h-[30px]   2xl:w-[120px] 2xl:h-[30px]  3xl:w-[150px]  3xl:h-[40px] ">{{condition}}</div>
                  </div>
                </header>

                <footer>
                  <div class="mb-2  text-gray-500  font-weight-black  xl:text-[12px]  1xl:text-[13px] 2xl:text-[14px]  3xl:text-[17px] ">Action:</div>
                  <div class="flex  justify-center">
                    <div class="flex  justify-center  items-center bg-red-300  xl:w-[70px] xl:h-[70px] 1xl:w-[80px]  1xl:h-[80px] 3xl:w-[100px]  3xl:h-[100px]  xl:px-1  2xl:px-2  3xl:px-2  rounded-full font-sans font-medium text-gray-700 text-[11px] 1xl:text-[11px]  2xl:text-[13px]  3xl:text-[15px]">  {{ template.action }}</div>
                  </div>
                </footer>

              </div>
              </div>
            </aside>



            <div class="flex  items-center  justify-center  h-[40px] xl:w-[520px] 1xl:w-[550px] 2xl:w-[700px] 3xl:w-[820px] " v-else>
              <p class="flex  items-center  justify-center  xl:w-[520px]  xl:h-[240px]  1xl:w-[550px]  1xl:h-[240px]  2xl:w-[800px]  3xl:w-[760px]  text-[#992121] text-[14px]  1xl:text-[16px]  3xl:text-[18px]">Please select both conditions and action before Deploy</p>
            </div>
          </div>

        </div>


                      <!-- Deploy and cancel btn -->    
        <div class="mt-[10px]">
          <button class="px-2  py-2  rounded-lg  text-sm  mx-[10px]  w-[100px]  text-white  bg-gradient-to-r from-green-400 to-green-600  hover:from-green-500 hover:to-green-700    transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5    shadow-blue-500/50" 
           @click="deployTemplate" :disabled="selectedCardIndex === null" :class="{ 'opacity-50 cursor-not-allowed': selectedCardIndex === null }">
            Deploy
          </button>

          <button class="px-2  py-2  rounded-lg  text-sm   mx-[10px]   w-[100px]    text-white bg-gradient-to-r from-red-400 to-red-600  hover:from-red-500 hover:to-red-700   transition-all duration-300 shadow-md hover:shadow-lg transform hover:-translate-y-0.5    shadow-red-500/50" 
           @click="unSelected" :disabled="selectedCardIndex === null" :class="{ 'opacity-50 cursor-not-allowed': selectedCardIndex === null }">
           Cancel
          </button>
        </div>

      </aside>

                       <!-- service locations  -->    
      <aside>
        <serviceLocationView class="relative top-[-420px] left-[25px] xl:top-[-10px] xl:left-[30px]  1xl:top-[10px] 1xl:left-[20px]  2xl:top-[0px] 2xl:left-[10px]  3xl:left-[30px]"/>
       </aside>
    </footer>
</main>
</template>



<script setup>
import serviceLocationView from './service-location.vue'
const { $toast} = useNuxtApp();
import { ref ,computed, onMounted} from "vue";
import axios from 'axios';

// Available conditions for dragging
const conditions = ref([
"Day", "Night","Parking", "Driving", "Battery < 30 %", "Battery < 90 %", "Speed > 30 km","Speed > 60 km","Speed > 100 km", 
  "Reverse", "Only Driver", "Neutral","With Passenger", "With Pet"
]);

// Available actions for dragging
const actions = ref([
"BMS >> Soc0", "Light On", "Camera On", "BMS >> Soc1", "Light Off", "Camera Off", "Window Open",
 "Air Conditioner On", "Lock Door", "Window Close","Air Conditioner Off","Unlock Door"
]);

// Default dropped conditions (pre-populated in the drop zone)
const droppedConditions = ref([]);

// Only one action can be dropped in this variable
const droppedAction = ref('');

// the current item being dragged
const draggedItem = ref(null);

// Array to store generated templates
const generatedTemplates = ref([]);


// the selected card index
const selectedCardIndex = ref(null);

//  when an item starts to be dragged
const onDragStart = (item) => {
draggedItem.value = item;
};


const isCancelEnabled = computed(() => {
return droppedConditions.value.length > 0 && droppedAction.value;
});



// Drop into the Conditions area (multiple items allowed)
const onDropConditions = () => {
if (draggedItem.value && conditions.value.includes(draggedItem.value)) {
  if (!droppedConditions.value.includes(draggedItem.value)) {
    droppedConditions.value.push(draggedItem.value);
  } else {
    $toast.info('You already dropped this condition. Select another.');
  }
} else {
  $toast.info('Only condition items are allowed here.');
}
draggedItem.value = null; // Reset after drop
};



// Drop into the Actions area (only one item allowed)
const onDropActions = () => {
if (draggedItem.value && actions.value.includes(draggedItem.value)) {
  if (!droppedAction.value) {
    droppedAction.value = draggedItem.value;
  } else if (droppedAction.value === draggedItem.value) {
    $toast.info('You already dropped this action. Select another.');
  } else {
    $toast.info('Only one action is allowed here. Remove the current action to drop another.');
  }
} else {
  $toast.info('Only action items are allowed here.');
}
draggedItem.value = null; // Reset after drop
};


// Remove a dropped condition
const removeCondition = (index) => {
droppedConditions.value.splice(index, 1);
};


// Remove the dropped action
const removeAction = () => {
droppedAction.value = null;
};


// Function to reset dropped conditions and action
const resetDroppedData = () => {
droppedConditions.value = [];
droppedAction.value = null;
};


// Create button logic to push the dropped data into the card section
const createTemplate = () => {
if (droppedConditions.value.length > 0 && droppedAction.value) {
  generatedTemplates.value.push({
    conditions: [...droppedConditions.value],
    action: droppedAction.value,
  });
  console.log(generatedTemplates)
  resetDroppedData();
} else {
  $toast.warning('Please select both conditions and action before creating')
}

};

// Cancel button logic to clear the dropped items
const cancelTemplate = () => {
if (droppedConditions.value.length > 0 && droppedAction.value) {
  resetDroppedData();
} 
else {
  $toast.warning('Please Select Both Conditions And Action Before Cancel')
}
};


// Select a card (single click)
const selectCard = (index) => {
selectedCardIndex.value = index;
};

// new Unselect a card in cancel button
const unSelected=()=>{
selectedCardIndex.value = null;
}

// Unselect a card (double click)
// const unselectCard = (index) => {
// if (selectedCardIndex.value === index) {
//   selectedCardIndex.value = null; // Unselect if double-clicked
// }
// };


// Remove the selected card from the templates
// const removeSelectedTemplate = () => {
// if (selectedCardIndex.value !== null) {
//   generatedTemplates.value.splice(selectedCardIndex.value, 1);
//   selectedCardIndex.value = null; // Reset selected index
// }
// };


// Save templates to localStorage
const saveTemplates = () => {
localStorage.setItem('templates', JSON.stringify(generatedTemplates.value));
$toast.success('Card list saved!.')

};


// when user click restore button. Restore templates from localStorage
const restoreTemplates = () => {
  const storedTemplates = localStorage.getItem('templates');
  console.log(storedTemplates); 
  // Check if templates exist in localStorage
  if (storedTemplates) {
    try {
      // Attempt to parse the stored templates
      const parsedTemplates = JSON.parse(storedTemplates);

      // If valid templates exist, restore them
      if (Array.isArray(parsedTemplates) && parsedTemplates.length > 0) {
        generatedTemplates.value = parsedTemplates;
        $toast.info('Card list restored!');
      } else {
        $toast.info('No card list found in local storage. Create and save cards.');
      }
    } catch (error) {
      console.error('Error parsing stored templates:', error);
      $toast.error('Error restoring card list from local storage.');
    }
  } else {
    // If nothing is stored in localStorage
    $toast.info('No card list found in local storage. Create and save cards.');
  }
};


// 
const restoreTemplatesPageReload = () => {
  const storedTemplates = localStorage.getItem('templates');
  // stored all card Templates
  console.log(storedTemplates); 
  if (storedTemplates) {
    try {
      const parsedTemplates = JSON.parse(storedTemplates);

      if (Array.isArray(parsedTemplates) && parsedTemplates.length > 0) {
        generatedTemplates.value = parsedTemplates;
      }
    } catch (error) {
      console.error('Error parsing stored templates:', error);
    }
  }
};

    // Automatically restore templates on component mount
    onMounted(() => {
      restoreTemplatesPageReload(); 
    });



// delete All Templates
const DeleteAllTemplates=()=>{
generatedTemplates.value = [];
console.log('Delete all cards...')
}


// Deploy to database
const deployTemplate = async () => {
if (selectedCardIndex.value !== null) {
  const selectedTemplate = generatedTemplates.value[selectedCardIndex.value];
  const yamlData = convertToYAML(selectedTemplate);
  console.log("Generated YAML:\n", yamlData);

   try {
  //   // Axios POST request to your backend API
  const response = await axios.post('http://10.221.47.46:4000/api/deploy', {
       yamlData: yamlData,  
      });
   console.log(yamlData)

    if (response.status === 200) {
       $toast.success('Piccolo config is deployed to the registry!');
       selectedCardIndex.value = null;
    } else {
      $toast.error('Failed to deploy config. Please try again.');
      }
  } catch (error) {
    console.error('Error deploying config:', error);
    $toast.error(`Error deploying config: ${error.message}`);
   }
} else {
  $toast.warning('Please select a template to deploy.');
}
};


// This Function to convert the selected template to YAML format

const convertToYAML = (template) => {
const currentDate = new Date();
const formattedDate = `${currentDate.getDate().toString().padStart(2, '0')}-${(currentDate.getMonth() + 1).toString().padStart(2, '0')}-${currentDate.getFullYear()}__${currentDate.getHours().toString().padStart(2, '0')}:${currentDate.getMinutes().toString().padStart(2, '0')}:${currentDate.getSeconds().toString().padStart(2, '0')}`;

return `
Date & Time: ${formattedDate}
Conditions:
- ${template.conditions.join("\n  - ")}
Action: ${template.action}
`;
};
</script>


<style scoped>


/* Styles for buttons when disabled */
.opacity-50 {
  opacity: 0.5;
}

.cursor-not-allowed {
  cursor: not-allowed;
}

.container {
  display: flex;
  justify-content: space-between;
}

.draggable {
  margin: 5px;
}

.dropped-item {
  position: relative;
}

.remove-icon {
  margin-left: 10px;
  color: red;
  cursor: pointer;
}

/* when user click card highlight the border */

.selected {
  border: 3px solid #28a745;
  background-color: #e6ffe6;
  box-shadow: 1px 1px 1px 3px rgb(200, 213, 198);
}

</style>

