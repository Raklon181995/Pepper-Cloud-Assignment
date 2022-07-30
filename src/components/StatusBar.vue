<template>
    <div class="mx-4 d-flex">
    <v-card class="my-4 mr-4" width="234px"
    v-for="statusInfo in statusInfos"
    :key="statusInfo.name">
        <div class="d-flex py-3 justify-space-between mx-3">
        <div class="pt-1">{{statusInfo.status}}</div>
        <div>
            <v-checkbox
              color="success"
              value="success"
              hide-details
            ></v-checkbox>
        </div>
        </div>
    </v-card>
    </div>
</template>
<script>
  export default {
         data: () => ({
             statusInfos: [
                 {status: "Status 1"}, {status: "New"}, {status: "Working"}, {status: "Nurturing"},{status: "Converted"},
                 
             ]
         })
  }

</script>
<style lang="scss" scoped>
.v-input--selection-controls{
    margin-top: 0px;
}

</style>