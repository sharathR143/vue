<template>
  <div>
    <p class="text-[20px] ml-3">service locations</p>
    <aside>
      <div class="gap-2 bg-blue-200 ml-10 flex justify-center items-center">
        <div v-for="host in hostnames" :key="host">
          <template v-if="selected && filteredParkingData.length > 0">
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
          </template>

          <div class="px-[20px] py-[10px] border-dashed border-black border-2">
            {{ host }}
          </div>
        </div>
      </div>
    </aside>
  </div>
</template>

<script setup>
import { onMounted } from "vue";
import Servicelocation from "../components/servicelocation.vue";
import Containerjson from "../data/container.json";

const props = defineProps(["drivingjson", "selected"]);
const hostnames = ["soc0", "soc1", "zcfront", "zcRear"];

const filteredParkingData = ref([]);
filteredParkingData.value = props.drivingjson;
onMounted(() => {
  console.log("filteredParkingData", filteredParkingData);
  console.log("selected", props.selected);
});
</script>
