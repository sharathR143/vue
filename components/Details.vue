<template>
  <div class="flex">
    <aside
      class="h-[500px] mt-5 w-[900px] bg-slate-200 ml-[40px] flex justify-center items-center"
    >
      <main class="flex justify-evenly mr-5">
        <!-- Driving -->
        <div
          class="flex gap-2 items-end bg-yellow-00 border-red-300 border-2"
          @click="sendData($event, filteredDrivingData)"
        >
          <div v-for="host in hostnames" :key="host">
            <div v-for="drivingData in filteredDrivingData" :key="drivingData">
              <div class="mb-4" v-if="drivingData.config['HostName'] == host">
                <div
                  v-for="name in drivingData.names"
                  :key="name"
                  class="px-[20px] py-[10px] border-dashed border-[red] border-2"
                >
                  {{ name }}
                </div>
              </div>
            </div>

            <div
              class="px-[20px] py-[10px] border-dashed border-black border-2"
            >
              {{ host }}
            </div>
          </div>
        </div>

        <!-- parking -->
        <div
          class="flex gap-2 items-end bg-blue-200 ml-10"
          @click="sendData($event, filteredParkingData)"
        >
          <div v-for="host in hostnames" :key="host">
            <div v-for="ParkingData in filteredParkingData" :key="ParkingData">
              <div class="mb-4" v-if="ParkingData.config['HostName'] == host">
                <div
                  v-for="name in ParkingData.names"
                  :key="name"
                  class="px-[20px] py-[10px] border-dashed border-[red] border-2"
                >
                  {{ name }}
                </div>
              </div>
            </div>

            <div
              class="px-[20px] py-[10px] border-dashed border-black border-2"
            >
              {{ host }}
            </div>
          </div>
        </div>
      </main>
    </aside>

    <aside class="h-[500px] mt-5 w-[500px] bg-slate-200 ml-[40px]">
      <Servicelocation :drivingjson="propsData" :selected="selected" />
    </aside>
  </div>
</template>

<script setup>
import Servicelocation from "../components/servicelocation.vue";
import driving from "../data/driving.json";
import parking from "../data/parking.json";

const json = ref(driving);
const parkingJson = ref(parking);

const filteredDrivingData = json.value.container.filter((element) => {
  return element.annotation["piccolo.package.name"] == "bms";
});

const filteredParkingData = parkingJson.value.container.filter((element) => {
  return element.annotation["piccolo.package.name"] == "bms";
});

const hostnames = ["soc0", "soc1", "zcfront", "zcRear"];

let propsData = ref(filteredDrivingData);

const selected = ref(false);

const sendData = (event, data) => {
  console.log("click");
  propsData.value = data;
  console.log(data);
  selected.value = true;
  //   selected.value = !selected.value;
};

console.log("filteredParkingData", filteredParkingData);
console.log("propsData", propsData.value);
</script>

<style scoped></style>
