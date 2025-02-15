<template>

    <div>{{ tags }}</div>

    <div>{{ tags.length }}</div>

    <div v-for="(tag, index) in tags" v-bind:id="index">{{ index + ' : ' + tag }}</div>

    <input type="text" :value="newTag" />

</template>

<script>
export default {

    data: () =>({

        tags: ['vue', 'react', 'angular'],

        newTag: "Laravel VueJs",
    })
}
</script>