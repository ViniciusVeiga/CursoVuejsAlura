<template>
    <button @click="dispara()" class="btn" :class="btnEstilo" :type="tipo">{{rotulo}}</button>
</template>

 <script>
 export default {
    props: {
        tipo: {
            required: true,
            type: String
        },      
        rotulo: {
            required: true,
            type: String
        },     
        confirmar: Boolean,
        estilo: String
    },

    methods: {
        dispara() {
            if(this.confirmar) {
                if(confirm('Confima a operação?')) {
                    this.$emit('button-ative');
                }
                return;
            }
            this.$emit('button-ative');
        }
    },

    computed: {
        btnEstilo() {
            if(this.estilo == "normal" || !this.estilo) return 'btn-normal';
            if(this.estilo == "alert") return 'btn-alert';
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

    .btn-alert {
        background: firebrick;
        color: white;
    }

    .btn-normal {
        background: darkcyan;
        color: white;
    }
 </style>
 
