<template>
  <v-app >
    <v-main class="background">
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
<style lang="scss">
.background{
  background-color: rgb(248, 248, 248);
}
</style>
