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


    methods: {

        handleChange(tags)
        {
            console.log('tags', tags);

            this.jsFrameworks = [...tags]
        }
    }


  }


</script>

<template>
    <h3>Hello VueJs</h3>
    {{ jsFrameworks }}
  <TagsInput :selectedTags="jsFrameworks" @change="handleChange" />

</template>

<style>

</style>
