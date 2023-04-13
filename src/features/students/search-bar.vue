<template>
    <div class="search">
        <input v-model="searchText" @input="handleInput" type="text" class="search-input" placeholder="Поиск">
        <img class="search-icon" src="@/assets/icons/search.svg" alt="search icon">
    </div>
</template>

<script>
export default {
    data() {
        return {
            searchText: ''
        }
    },
    methods: {
        handleInput() {
            this.$emit('input', this.searchText)
        },
    }
}
</script>

<style scoped>
.search {
    position: relative;
    margin-top: 20px;
}

.search-icon {
    position: absolute;
    left: 16px;
    top: 18.35px;
}

.search-input {
    width: 100%;
    border: none;
    font-size: var(--font-size-3);
    border-radius: 4px;
    padding: 16.5px;
    color: var(--black);
    padding-left: 38px;
    border: 1px solid var(--blue-light);
}

.search-input::placeholder {
    color: var(--medium);
}

.search-input:hover {
    border: 1px solid var(--blue05);

}

.search-input:focus {
    outline: none;
    border: 1px solid var(--blue);
}

.search-input::before {
    content: url(@/assets/icons/search.svg);
    display: block;
    position: absolute;
}
</style>