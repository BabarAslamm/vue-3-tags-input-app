<template>

    <div>{{ tags }}</div>

    <div>{{ tags.length }}</div>

    <div v-for="(tag, index) in tags" v-bind:id="index">
        {{ tag }}
        <a @click.prevent="removeTag(index)" href="#">x</a>
    </div>

    <hr>

    <input 
        type="text" 
        v-model.trim="newTag" 
        v-on:keydown.enter="addNewTag" 
        @keydown.tab.prevent="addNewTag"
        @keydown.delete="removeLastTag" 
        :class="{'tag-exists':isTagExists }"
    />

    <p>newTag : {{ newTag }}</p>

    

</template>

<script>
export default {

    data: () =>({

        tags: ['vue', 'react', 'angular'],

        newTag: "",
    }),

    computed: {

        isTagExists(){

           return this.tags.includes(this.newTag);
        }
    },

    methods: {

        addNewTag() {

            if(this.newTag && !this.isTagExists){

                this.tags.push(this.newTag);

                this.newTag = '';
            }
        },

        removeTag (index) {

            this.tags.splice(index, 1);
        },

        removeLastTag() {

            if(this.newTag.length === 0){

                this.removeTag(this.tags.length -1);

            }
            
        }

    }
}
</script>

<style scoped>
.tag-exists {
    color: red; 
    text-decoration: line-through;
}
</style>