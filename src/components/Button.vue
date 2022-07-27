<template>
    <button @click="onClick()" :style="{background: color}" class="btn">{{text}}</button>
    <!-- instead of v-on:click we could write it as @click -->
</template>

<script>
    export default{
        name: 'Button',
        props:{
            text: String,
            color: String
        },
        methods: {
            onClick(){
                console.log('clicked');
            },
        }
    }
</script>