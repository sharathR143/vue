<template>
  <div class="flex">
    <h4>{{ server }}</h4>
    <h4>{{ ECU }}</h4>
    <h4>{{ VM }}</h4>
  </div>
</template>


<script>
export default {
  name: "Details",
  data() {
    return {
      server: "The Number of service Limitation is 10",
      ECU: "ECU : 6",
      VM: "5 VMs on Each ECU",
    };
  },
};
</script>

<style scoped>
.flex{
  display: flex;
  margin-right: 40px;
  margin-top: 60px;
  
}
.flex h2{
 margin-right: 30px;
  
}
</style>
