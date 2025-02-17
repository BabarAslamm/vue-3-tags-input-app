<script >
  // import TagsInput from "./components/TagsInput.vue";

  // export default {
  //   components: {
  //     TagsInput
  //   }
  // }

  export default {

    data:() => ({

        jsFrameworks : ["vue", "react", "angular"],

    }),

    mounted() {

        setTimeout(() => {
            this.jsFrameworks.push('NextJS')
        }, 300);
    },
  }


</script>

<template>

  <TagsInput :selectedTags="jsFrameworks" />

</template>

<style>

</style>
