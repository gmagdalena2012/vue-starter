<template>
    <div>
        <h2>Witaj {{ username }}</h2>
        <button @click="$emit('logout')" class="float-right  button-outline button">Wyloguj</button>
        </h2>
    </div>
</template>

<script>
    export default {
        props: ['username'],
        methods: {
            logMeOut() {
                this.$emit('logout');
            }
        }
    }
</script>
