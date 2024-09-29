<template>
  <div>
    <p class="text-[20px] ml-3">service locations</p>
    <aside class="flex justify-evenly mr-5">
      <div class="flex gap-2 items-end bg-yellow-00 border-red-300 border-2">
        <div
          v-if="selecttype == 'driving'"
          class="flex gap-2 items-end bg-blue-200 ml-10"
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

        <div v-else class="flex gap-2 items-end bg-blue-200 ml-10">
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
      </div>
    </aside>
  </div>
</template>

<script setup>
import { computed } from "vue";
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

const props = defineProps(["drivingjson", "selected", "selecttype"]);

console.log("slected-type", props.selected.value);

const hostnames = ["soc0", "soc1", "zcfront", "zcRear"];
</script>
