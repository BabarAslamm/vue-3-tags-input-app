<template>

    <div>{{ tags }}</div>

    <div>{{ tags.length }}</div>

    <div v-for="(tag, index) in tags" v-bind:id="index">{{ index + ' : ' + tag }}</div>

    <hr>

    <input 
        type="text" 
        v-model="newTag" 
        v-on:keydown.enter="tags.push(newTag)" 
        @keydown.tab.prevent="tags.push(newTag)" 
    />

    <p>newTag : {{ newTag }}</p>

    

</template>

<script>
export default {

    data: () =>({

        tags: ['vue', 'react', 'angular'],

        newTag: "",
    })
}
</script>