<script setup>
    const props = defineProps(['tarefas']);

import { computed } from 'vue';

const tarefasPendentes = computed(() => {
  return props.tarefas.filter(tarefa => !tarefa.finalizada).length;
});

</script>
<template>
    <p v-if="tarefasPendentes === 0" class="text-center text-success">
    Não há mais tarefas pendentes!
    </p>
    <ul class="list-group mt-4" v-else>
        <li class="list-group-item" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
        <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
        <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
            {{ tarefa.titulo }}
        </label>
        </li>
    </ul>
</template>

<style scoped>
.done {
    text-decoration: line-through;  
}
</style>