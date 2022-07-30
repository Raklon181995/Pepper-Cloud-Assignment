<template>
    <div class="mx-4">
        <div class="pt-4 d-flex">
     <template>
        <v-text-field
          v-model="search"
          label="Filter by date"
          class="mx-4"
          append-icon="mdi-magnify"
          outlined   dense
        ></v-text-field>
      </template>
        </div>
        <hr class="my-3">
        <div class="pb-3">
            
            <v-card
             outlined
            class="mx-auto my-5"
             v-for="detail in filterArray"
             :key="detail.name">
                <div class="d-flex">
                    <v-col class="col-2">
                         <img src="@/assets/Images/Ellipse.svg" class="mt-5 ml-1" alt="logo" width="40px" />
                    </v-col>
                    <v-col class="col-9">
                        <div class="font-14 mt-2">{{detail.taskName}}</div>
                        <div class="font-12 text-gray">{{detail.text}}
                            <span class="text-yellow">{{detail.name}}</span>
                        </div>
                        <div class="font-12 text-gray">
                            {{detail.date}}
                        </div>
                    </v-col>
                </div>
                <div >
                    <div class="justify-center"
                        align="center">
                    <v-btn
                        icon
                        @click="show = !show"
                        
                    >
                        <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
                    </v-btn>
                    </div>

                    <v-expand-transition>
                    <div v-show="show">
                        <v-divider></v-divider>

                        <v-card-text>
                        I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
                        </v-card-text>
                    </div>
                    </v-expand-transition>
                </div>
            </v-card>
        </div>
    </div>
</template>
<script>
  export default {
    data: () => ({
      show: false,
      search: '',
      filter: {
      name: '',
       
      },
      details: [
          {
              taskName: "Informed Product Feature",
              text: "You contacted with",
              name: "Rakesh Lonikar",
              date: '18 Feb 2022',
          },
          {
              taskName: "Send Product Brochure",
              text: "You added a To Do task with",
              name: "Raklon",
              date: '22 Feb 2022',
          },
           {
              taskName: "Send Product Brochure",
              text: "You added a To Do task with",
              name: "Raklon",
              date: '28 Feb 2022',
          },
           {
              taskName: "Informed Product Feature",
              text: "You contacted with",
              name: "Rakesh Lonikar",
              date: '29 Feb 2022',
          },

      ],
    }),
      
    computed:{
        filterArray:function(){
            return this.details.filter((detail)=>{
                return detail.date.match(this.search);
            });
        }
    }
  }
</script>
<style lang="scss" scoped>
.font-14{
    font-size: 14px;
    font-weight: 500;
}
.font-12{
    font-size: 12px;
}
.text-gray{
    color: rgb(146, 142, 142);
}
.text-yellow{
    color: rgb(209, 127, 40);
}

</style>