<template>
  <HPC />
  <div class="center">
    <Detail />
  </div>
  <!-- <drag /> -->
</template>

<script>
import HPC from "./components/HPC.vue";
import Detail from "./components/Details.vue";
// import drag from "./components/drag.vue";
export default {
  name: "app",
  data() {
    return {};
  },
  components: {
    HPC,
    Detail,
    // drag,
  },
};
</script>

<style scoped>
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  /* margin-top: 50px; */
}
</style>
