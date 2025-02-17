<template>
    <h3>Tags</h3>
    <div class="tags-container">
        
        <span v-for="(tag, index) in tags" :key="index" class="tag">
            {{ tag }}
            <a @click.prevent="removeTag(index)" href="#" class="tag-remove">&times;</a>
        </span>
        <input 
            type="text" 
            v-model.trim="newTag" 
            v-on:keydown.enter="addNewTag" 
            @keydown.tab.prevent="addNewTag"
            @keydown.delete="removeLastTag" 
            :class="{'tag-exists': isTagExists }"
            class="tag-input"
            placeholder="Add a tag..."
        />
    </div>

    <p>newTag : {{ newTag }}</p>
</template>

<script>
export default {
    data: () => ({
        tags: ['vue', 'react', 'angular'],
        newTag: "",
    }),
    watch: {
        newTag(newVal) {
            if (newVal.indexOf(",") > -1) {
                this.newTag = this.newTag.slice(0, -1);
                this.addNewTag();
            }
        }
    },
    computed: {
        isTagExists() {
            return this.tags.includes(this.newTag);
        }
    },
    methods: {
        addNewTag() {
            if (this.newTag && !this.isTagExists) {
                this.tags.push(this.newTag);
                this.newTag = '';
            }
        },
        removeTag(index) {
            this.tags.splice(index, 1);
        },
        removeLastTag() {
            if (this.newTag.length === 0) {
                this.removeTag(this.tags.length - 1);
            }
        }
    }
}
</script>

<style scoped>
.tags-container {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    background: #f9f9f9;
}

.tag {
    display: inline-flex;
    align-items: center;
    background-color: #e0e0e0;
    color: #333;
    padding: 0.3em 0.7em;
    border-radius: 2em;
    font-size: 0.9em;
    margin: 0.2em;
    transition: background 0.3s;
}

.tag:hover {
    background-color: #d0d0d0;
}

.tag-remove {
    margin-left: 0.5em;
    color: #888;
    cursor: pointer;
    text-decoration: none;
}

.tag-remove:hover {
    color: #555;
}

.tag-input {
    flex: 1;
    border: none;
    outline: none;
    min-width: 100px;
    padding: 0.3em;
    font-size: 0.9em;
    background: transparent;
}

.tag-input.tag-exists {
    color: red;
    text-decoration: line-through;
}

.tag-input::placeholder {
    color: #aaa;
    opacity: 0.7;
}

.tag-input:focus {
    outline: none;
    border-bottom: 2px solid #007bff;
}

.tag {
    transition: transform 0.2s ease-in-out;
}

.tag-remove:focus {
    outline: none;
}
</style>
