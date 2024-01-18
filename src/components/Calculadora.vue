<script setup>
const props = defineProps(['atualizaNumero1', 'atualizaNumero2', 'atualizaOperador', 'operadoresValidos', 'resultado'])
</script>

<template>
    <div class="row" style="justify-content: center">
        <div class="col-md-1">
            <input id="numero1" type="number" class="form-control border-dark semseta" @keyup="props.atualizaNumero1">
        </div>
        <div class="col-md-1">
            <select id="operador" class="form-select border-dark" @change="props.atualizaOperador">
                <option value="mais">+</option>
                <option value="menos">-</option>
                <option value="vezes">x</option>
                <option value="divisao">div</option>
            </select>
        </div>
        <div class="col-md-1">
            <input type="number" id="numero2" class="form-control border-dark semseta" @keyup="props.atualizaNumero2">
        </div>
        <div class="col-md-1">
            <h5 class="">=</h5>
        </div>
        <div class="col-md-3">
            <label v-if="props.operadoresValidos" class="h2">
                {{ props.resultado }}
            </label>
            <label v-else class="h2">
                Aguardando parâmetros...
            </label>
        </div>
    </div>
</template>

<style scoped>
.semseta::-webkit-inner-spin-button {
    -webkit-appearance: none;
}

.semseta {
    -moz-appearance: textfield;
}
</style>