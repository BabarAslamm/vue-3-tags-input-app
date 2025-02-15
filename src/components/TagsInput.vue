<template>

    <div>{{ tags }}</div>

    <div>{{ tags.length }}</div>

    <div v-for="(tag, index) in tags" v-bind:id="index">{{ index + ' : ' + tag }}</div>

    <input 
        type="text" 
        :value="newTag" 
        v-on:keydown.enter="tags.push($event.target.value)" 
        @keydown.tab.prevent="tags.push($event.target.value)" 
    />

    

</template>

<script>
export default {

    data: () =>({

        tags: ['vue', 'react', 'angular'],

        newTag: "",
    })
}
</script>