<template>
    <form @submit.prevent id="roll-buttons">
        <button @click="rollDice" class="btn">Roll!</button>
        <button @click="resetDice" class="btn">Reset</button>
    </form>
</template>

<script>
    export default {
        methods: {
            rollDice() {
                this.$emit('die-rolled') // trigger dice being added into roll array
            },
            resetDice() {
                this.$emit('dice-reset') // trigger full reset of dice
            },
        },
    };
</script>

<style scoped>
    form button{
        margin:15px;
        padding:1em;
    }
</style>