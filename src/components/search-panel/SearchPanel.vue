<template>
    <div>
        <input type="text" class="form-control search-input" placeholder="Kinolarni qidirish">
    </div>
</template>

<script>
    export default {
        name: 'search-panel',
        data() {
            return {
                
            }
        }
    }
</script>

<style scoped>
.search-input {
    margin-bottom: 1rem;
    padding: 1.2rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(3, 82, 62, 0.215);
}
</style>