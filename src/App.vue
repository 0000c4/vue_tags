<template>
  <v-app>
    <v-container class="demo_container">
      <Tags :tags="tags" :align_to_width="false" />
      <Tags :tags="tags" :align_to_width="true" />
      <div class="half_container">
        <Tags :tags="tags" :align_to_width="false" />
        <Tags :tags="tags" :align_to_width="true" />
      </div>
    </v-container>

    <v-container class="demo_container">
      <Tags :tags="tags2" :align_to_width="false" />
      <Tags :tags="tags2" :align_to_width="true" />
      <div class="half_container">
        <Tags :tags="tags2" :align_to_width="false" />
        <Tags :tags="tags2" :align_to_width="true" />
      </div>
    </v-container>

  </v-app>
</template>

<script>
import Tags from './components/Tags';

export default {
  name: 'App',

  components: {
    Tags,
  },
  data: () => ({
    tags: [
      { icon: "mdi-star-outline", text: "4,3" },
      { text: "Фридландские ворота" },
      { text: "1,2км от вас" },
    ],
    tags2: [
      { icon: "mdi-star", text: "test 1" },
      { icon: "mdi-circle", text: "test 2" },
      { icon: "mdi-square", text: "test 3" },
      { icon: "mdi-star", text: "test 4" },
      { icon: "mdi-circle", text: "test 5" },
      { icon: "mdi-square", text: "test 6" },
      { icon: "mdi-star", text: "test 7" },
      { text: "test 8" },
      { icon: "mdi-square", text: "test 9" },
      { icon: "mdi-star", text: "test 10" },
      { text: "test 11" },
      { icon: "mdi-square", text: "test 12" },
    ]
  }),
};
</script>

<style scoped lang="scss">
.container {
  all: unset;
}
.demo_container{
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.half_container{
  width: 50%;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
