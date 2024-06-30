<template>
    <div ref="tags" class="tags_container" :class="align_to_width && 'align_to_width'">
      <div v-for="tag in processed_tags" v-bind:key="tag.text" class="tags_column">
        <v-icon v-if="tag.dot">mdi-circle-small</v-icon>
        <v-icon v-if="tag.icon">{{ tag.icon }}</v-icon> <span v-if="tag.text">{{ tag.text }}</span>
      </div>
    </div>
</template>

<script>
export default {
  props: {
    tags: [],
    align_to_width: Boolean
  },
  data: () => {
    return {
      processed_tags: []
    }
  },
  created() {
    window.addEventListener("resize", this.processTags);
  },
  destroyed() {
    window.removeEventListener("resize", this.processTags);
  },
  mounted() {
    this.processTags();
  },
  methods: {
    processTags() {
      this.processed_tags = []
      for (const [index, tag] of this.tags.entries()) { //add dots
        this.processed_tags.push(tag)
        if (index !== this.tags.length - 1)
          this.processed_tags.push({ dot: true })
      }
      this.$nextTick(() => {
        const container = this.$refs.tags //get tags container
        let width_all = 0; //sum of widths
        for (const [index, node] of container.childNodes.entries()) {
          if (width_all + node.offsetWidth <= container.offsetWidth) {
            width_all += node.offsetWidth
          }
          else {
            this.processed_tags.splice(index)
            if (this.processed_tags.length > 0 && this.processed_tags[index - 1].dot) {
              this.processed_tags.splice(index - 1)
            }
            break
          }
        }
      });

    },
  }


} 
</script>
<style scoped lang="scss">
.tags_container {
  display: flex;
  flex-wrap: nowrap;

  &.align_to_width {
    justify-content: space-between;
  }
}

.tags_column {
  display: flex;
  align-items: center;
  flex-wrap: nowrap;
  text-wrap: nowrap;

}
</style>
