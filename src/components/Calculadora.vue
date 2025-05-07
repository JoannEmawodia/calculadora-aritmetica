<template>
    <div class="container mt-5">
        <div class="card p-4 shadow-sm">
            <h2 class="mb-4">Calculadora Aritmética</h2>

            <div class="form-group">
                <label>Número 1:</label>
                <input type="number" v-model.number="state.num1" class="form-control" />
            </div>

            <div class="form-group">
                <label>Número 2:</label>
                <input type="number" v-model.number="state.num2" class="form-control" />
            </div>

            <div class="form-group">
                <label>Operação:</label>
                <select v-model="state.operacao" class="form-control">
                    <option value="+">Adição (+)</option>
                    <option value="-">Subtração (-)</option>
                    <option value="*">Multiplicação (*)</option>
                    <option value="/">Divisão (/)</option>
                </select>
            </div>

            <hr />
            <h4>Resultado: {{ resultado }}</h4>
        </div>
    </div>
</template>

<script setup>
import { reactive, computed } from 'vue';

const state = reactive({
    num1: 0,
    num2: 0,
    operacao: '+'
});

const resultado = computed(() => {
    switch (state.operacao) {
        case '+':
            return state.num1 + state.num2;
        case '-':
            return state.num1 - state.num2;
        case '*':
            return state.num1 * state.num2;
        case '/':
            return state.num2 !== 0 ? (state.num1 / state.num2).toFixed(2) : 'Erro (divisão por zero)';
        default:
            return 'Operação inválida';
    }
});

</script>