<template>
    <div class="cliente" :class="{ 'cliente-normal': !isPremium, 'cliente-premium': isPremium }">
        <!-- <input type="text" v-model="cliente.nome">
        <hr>
        <input type="text" v-model="cliente.descricao"> -->
        <p>Nome: {{ cliente.nome }}</p>
        <p style="width: 100%">Descrição: {{ cliente.descricao }}</p>
        <button @click="mudarCor()">Mudar a Cor</button>
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
    },
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
}
.cliente-normal {
    background-color: aquamarine;
}
.cliente-premium {
    background-color: gold;
}
</style>