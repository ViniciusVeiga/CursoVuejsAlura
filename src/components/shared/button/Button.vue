<template>
    <button @click="dispara()" class="btn btn-perigo" :type="tipo">{{rotulo}}</button>
</template>

 <script>
 export default {
    props: ['tipo', 'rotulo'],

    methods: {
        dispara() {
            this.$emit('button-ative');
        }
    }
 }
 </script>
 
 <style scoped>
    .btn {
        display: inline-block;
        padding: 10px;
        border-radius: 3px;
        margin: 10px;
        font-size: 1.2em;
    }

    .btn-perigo {
        background: firebrick;
        color: white;
    }

    .btn-padrao {
        background: darkcyan;
        color: white;
    }
 </style>
 
