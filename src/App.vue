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

        backendFrameworks : ['Laravel'],

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
    <h3>Frontend Framework</h3>
    <div>{{ jsFrameworks }}</div>
  <TagsInput :selectedTags="jsFrameworks" @change="handleChange" />

  <h3>Backend Framework</h3>
    <div>{{ backendFrameworks }}</div>
  <TagsInput :selectedTags="backendFrameworks" @change="backendFrameworks=[...$event]" />

</template>

<style>

</style>
