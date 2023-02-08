<template>
  <div class="container">
    <h2>{{ titulo }}</h2>
    <div class="input-group">
      <input v-model="novaTarefa" type="text" @keyup.enter = "adicionarTarefa">
      <span class="input-group-btn">
        <button @click="adicionarTarefa" class="btn" btn-primary>Adicionar tarefa</button>
      </span>
    </div>
    <ul>
      <li v-for="(tarefa, index) in tarefas" :key="index" :class="{'removed': tarefa.checked}">
        <input type="checkbox" v-model="tarefa.checked">
        <label>{{ tarefa.titulo }}</label>
      </li>
    </ul>

    <footer>
    <em>Altere aqui o título da sua lista de tarefas</em>
    <input v-model="titulo" type="text" />
  </footer>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      titulo: "Minha lista de tarefas",
      tarefas: [
        {
          titulo: "Ler", checked: true
        },
        {
          titulo: "Estudar", checked: false
        },
        {
          titulo: "Programar", checked: true
        }
      ],
      novaTarefa: ''
    }
  },
  methods: {
    adicionarTarefa() {
      this.tarefas.push({
        titulo: this.novaTarefa,
        checked: false
      });
      this.novaTarefa = '';
    }
  }
}
</script>

<style>
.container {
  width: 60%;
  margin: 20px auto 0 auto;
}

ul li {
  list-style: none;
}

.removed {
  color: grey;
}

.removed label {
  text-decoration: line-through;
}
</style>
