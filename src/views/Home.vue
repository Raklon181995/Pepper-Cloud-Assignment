<template>
  <div>
    <v-card class="d-flex justify-space-between ma-4">
      <!-- <div class="pa-4">Status 1</div>
      <div class="pa-4">New</div>
      <div class="pa-4">Working</div>
      <div class="pa-4">Nurturing</div>
      <div class="pa-4">Converted</div> -->
      <StatusBar />
    </v-card>
  <div>
    <div class="mx-4 mt-6 justify-left" align="left">
      <v-tabs
        v-model="tab"
        fixed-tabs
        height="35px"
        class="tab-section"
        show-arrows
      >
        <v-tabs-slider color="orange" class="tab-slider"></v-tabs-slider>
        <v-tab v-for="item in items" :key="item.tab" :href="'#' + item.name"
        class="background">
          {{ item.name }}
        </v-tab>
      </v-tabs>
    </div>
    <hr class="mx-4">
    <v-tabs-items v-model="tab" >
      <v-tab-item v-for="item in items" :key="item.tab" :value="item.name"
      class="background">
        <div v-if="item.tab === 'ACTIVITY'">
          <Activity />
        </div>
        <div v-if="item.tab === 'INFORMATION'">
          <Information />
        </div>
      </v-tab-item>
    </v-tabs-items>
  </div>
  </div>
</template>

<script>
import Activity from "@/components/Activity.vue";
import StatusBar from "@/components/StatusBar";
import Information from "@/components/Information.vue";
export default {
  components: {
    Activity,
    StatusBar,
    Information,
  },
  data() {
    return {
      tab: null,
      items: [
        { tab: "ACTIVITY", name: "Activity" },
        { tab: "INFORMATION", name: "Information" },
      ],
    };
  },
  methods: {},
};
</script>
<style lang="scss">
.tab-section{
  width: 300px !important;
   .v-tab--active {
    color: rgb(212, 84, 10) !important;
    border-radius: 6px 6px 6px 6px;
  }
}

</style>
