<template>
    <div class="cliente" :class="{ 'cliente-normal': !isPremium, 'cliente-premium': isPremium }">
        <!-- <input type="text" v-model="cliente.nome">
        <hr>
        <input type="text" v-model="cliente.descricao"> -->
        <p>Nome: {{ cliente.nome | processarNome}}</p>
        <p style="width: 100%">Descrição: {{ cliente.descricao }}</p>
        <button class="button is-primary" @click="emitirEventoDeletar()">Deletar</button>
        <button class="button is-primary" @click="mudarCor()">Mudar a Cor</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            isPremium: false,
        };
    },
    props: {
        cliente: Object,
    },
    methods: {
        mudarCor: function () {
            this.isPremium = !this.isPremium;
            console.log("Click");
        },
        emitirEventoDeletar: function() {
            this.$emit("meDelete", this.cliente.id);
        },
    },
    filters: {
        processarNome: function(value) {
            return value.toUpperCase();
        }
    }
};
</script>

<style scoped>
.cliente {
    width: 250px;
    height: 200px;
    display: flex;
    justify-content: center;
    text-align: center;
    flex-wrap: wrap;
    color: darkblue;
    flex-grow: 4;
    border-radius: 10px;
    border: solid black 2px;
    margin: 10px;
}
.cliente-normal {
    background-image: linear-gradient(to bottom right, aquamarine, rgba(72, 72, 221, 0.795));
    
}
.cliente-premium {
    background-image: linear-gradient(to bottom right, rgb(249, 250, 177), gold);
}
</style>