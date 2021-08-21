<template>
  <h1>{{ titulo }}</h1>
  <input
    v-model="tarefa.descricao"
    type="text"
    placeholder="Descrição da tarefa"
  />
  <!--   <button @click="adicionarTarefa">Adicionar</button>
 -->
 <app-btn texto="Adicionar" @click="adicionarTarefa"></app-btn>

  <table border="1">
    <thead>
      <th>Concluída</th>
      <th>Descrição</th>
    </thead>
    <tr
      v-for="iterador in tarefas"
      :key="iterador"
      :class="{ riscado: iterador.concluida }"
    >
      <td>
        <input type="checkbox" v-model="iterador.concluida" />
      </td>
      <td>{{ iterador.descricao }}</td>
    </tr>
  </table>
</template>
<script>

import AppBtn from './components/AppBtn.vue'

export default {
  components: {
    AppBtn
  },

  data() {
    return {
      titulo: "ToDoList Vite",
      tarefas: [],
      tarefa: {
        descricao: "",
        concluida: false,
      },
    };
  },
  methods: {
    adicionarTarefa() {
      this.tarefas.push(Object.assign({}, this.tarefa));
    },
  },
};
</script>

<style>
.riscado {
  text-decoration: line-through;
}
</style>