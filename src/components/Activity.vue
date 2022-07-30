<template>
<div>
    <v-row>
        <v-col class="col-8 px-0 ml-3">
            <v-card class="mx-4 my-6">
                <div class="justify-left" align="left">
                <v-tabs
                    v-model="tab"
                    fixed-tabs
                    height="35px"
                    class="tab-section-card py-2"
                    show-arrows
                >
                    <v-tabs-slider color="orange" class="tab-slider background"></v-tabs-slider>
                    <v-tab v-for="item in items" :key="item.tab" :href="'#' + item.name">
                    {{ item.name }}
                    </v-tab>
                </v-tabs>
                </div>
                <hr>
                <div>
                <v-tabs-items v-model="tab" class="mt-3">
                <v-tab-item v-for="item in items" :key="item.tab" :value="item.name" >
                    <div v-if="item.tab === 'TASKS'">
                      <Task />
                    </div>
                    <div v-if="item.tab === 'EVENT'">
                      <div class="text-center">Event Section</div>
                    </div>
                    <div v-if="item.tab === 'MAKENOTE'">
                      <div class="text-center">Make Note Section</div>
                    </div>
                    <div v-if="item.tab === 'ATTACHMENT'">
                      <div class="text-center">Attachment</div>
                    </div>
                    <div v-if="item.tab === 'ACTIVITYSET'">
                      <div class="text-center">Activity Set</div>
                    </div>
                    <div v-if="item.tab === 'CUSTOMFIELD'">
                      <div class="text-center">Custom Field</div>
                    </div>
                </v-tab-item>
                </v-tabs-items>
                </div>
            </v-card>
        </v-col>
        <v-col class="px-0 mr-6">
            <v-card class="my-6">
                   <FilterSection />
            </v-card>
        </v-col>
    </v-row>
 
 
</div>
</template>

<script>
import Task from "@/components/Task.vue";
import FilterSection from "@/components/FilterSection.vue";
// import Information from "@/components/Information.vue";
export default {
  components: {
    Task,
    FilterSection,
    // Information,
  },
  data() {
    return {
      tab: null,
      items: [
        { tab: "TASKS", name: "Tasks" },
        { tab: "EVENT", name: "Event" },
        { tab: "MAKENOTE", name: "Make Note" },
        { tab: "ATTACHMENT", name: "Attachment" },
        { tab: "ACTIVITYSET", name: "Activity" },
        { tab: "CUSTOMFIELD", name: "Custom" },
      ],
    };
  },
  methods: {},
};
</script>
<style lang="scss">
.tab-section-card {
  border: 1px solid #dcdcdc;
  box-sizing: border-box;

  width: 100%;
  .v-tab--active {
    background: rgb(243, 217, 131);
    color: rgb(145, 112, 5) !important;
  }
}


</style>
