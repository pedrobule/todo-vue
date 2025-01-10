<script setup>
    const props = defineProps(['cadastraTarefa', 'tarefaTemporaria', 'trocarFiltro', 'editaTarefaTempo']);
</script>

<template>
<form @submit.prevent="props.cadastraTarefa">
    <div class="row">
        <div class="col">
        <input :value="props.tarefaTemporaria" @change="props.editaTarefaTempo" required 
            type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control">
        </div>
        <div class="col-md-2">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
        </div>
        <div class="col-md-2">
        <select @change="props.trocarFiltro" class="form-control">
            <option value="todas">Todas as tarefas</option>
            <option value="pendentes">Pendentes</option>
            <option value="finalizadas">Finalizadas</option>
        </select>
        </div>
    </div>
    </form>
</template>