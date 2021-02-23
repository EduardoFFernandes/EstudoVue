<template>
    <div id="app">
        <h1>Clientes</h1>
        <div class="clientes">
          <div v-for="cliente in clientes" :key="cliente.id">
              <Cliente :cliente="cliente" />
          </div>
        </div>
    </div>
</template>

<script>
import Cliente from "./components/Cliente";
export default {
    name: "App",
    data() {
        return {
            clienteEduardo: {
                nome: "Eduardo Freire Fernandes",
                descricao: "Descricao do objeto",
            },
            clientes: [
                {
                    id: 1,
                    nome: "Eduardo Freire Fernandes",
                    descricao: "Descricao 1",
                },
                {
                    id: 2,
                    nome: "Fernando Freire Fernandes",
                    descricao: "Descricao 2",
                },
                {
                    id: 3,
                    nome: "Joao Freire Fernandes",
                    descricao: "Descricao 3",
                },
                {
                    id: 4,
                    nome: "Gabriel Freire Fernandes",
                    descricao: "Descricao 4",
                },
                {
                    id: 5,
                    nome: "Allison Freire Fernandes",
                    descricao: "Descricao 5",
                },
            ],
        };
    },
    components: {
        Cliente,
    },
};
</script>

<style scoped>
  #app {
    text-align: center;
  }
  .clientes {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    margin: 0px 10% 0px 10%;
  }
</style>