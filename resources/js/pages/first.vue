<template>
    <h1>{{ greeting }}</h1>
    <a v-bind:href="'add'">Add</a>
    <second/>
</template>
<script>
import second from './second';
export default {
    setup: () => ({
        greeting: 'Hello World from Vue 3!'
    }),

    components:{
    	second
    }
}
</script>
