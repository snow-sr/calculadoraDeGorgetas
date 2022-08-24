<script>
export default {
  data() {
    return {
      qualidadeDoServico: "",
      Servico: "",
      Pagar: "",
      valorFinalPorPessoa: "",
    };
  },
  methods: {
    calcularValorComGorjeta() {
      let porcentagemDaGorjeta = parseInt(this.qualidadeDoServico) / 100;
      let valorDoServico = parseInt(this.Servico);
      let qntdPessoasPagar = parseInt(this.Pagar);

      const valorComGorjeta =
        valorDoServico + valorDoServico * porcentagemDaGorjeta;

      this.valorFinalPorPessoa = valorComGorjeta / qntdPessoasPagar;
    },
  },
};
</script>

<template>
  <div
    class="w-full rounded-xl bg-white p-4 shadow-2xl text-black shadow-white/40"
  >
    <div class="mb-4 grid grid-cols-2 gap-4">
      <div class="flex flex-col">
        <label for="text" class="mb-2 font-semibold"
          >Qualidade do serviço:
        </label>
        <select
          id="text"
          v-model="qualidadeDoServico"
          class="w-full max-w-lg rounded-lg border border-slate-200 px-2 py-1 hover:border-blue-500 focus:outline-none focus:ring focus:ring-blue-500/40 active:ring active:ring-blue-500/40"
        >
          <option value="30">Excepcional</option>
          <option value="25">Mais que bom</option>
          <option value="20">Bom</option>
          <option value="15">Ok</option>
          <option value="10">Ruim</option>
          <option value="5">Péssimo</option>
        </select>
      </div>
      <div class="flex flex-col">
        <label for="text" class="mb-2 font-semibold">Valor do serviço:</label>
        <input
          type="number"
          class="w-full max-w-lg rounded-lg border border-slate-200 px-2 py-1 hover:border-blue-500 focus:outline-none focus:ring focus:ring-blue-500/40 active:ring active:ring-blue-500/40"
          v-model="Servico"
        />
      </div>
    </div>

    <div class="mb-4 flex flex-col">
      <label for="age" class="mb-2 font-semibold"
        >Quantas pessoas pagarão?</label
      >
      <input
        type="number"
        v-model="Pagar"
        class="w-full max-w-[200px] rounded-lg border border-slate-200 px-2 py-1 hover:border-blue-500 focus:outline-none focus:ring focus:ring-blue-500/40 active:ring active:ring-blue-500/40"
      />
    </div>

    <div>
      <button
        type="button"
        class="max-w-lg bg-gray-300 font-mono rounded-lg border border-slate-800 px-2 py-1 hover:border-blue-500 focus:outline-none focus:ring focus:ring-blue-500/40 active:ring active:ring-blue-500/40"
        @click="calcularValorComGorjeta"
      >
        Calcular
      </button>
    </div>
    <div v-if="valorFinalPorPessoa">
      <p class="text-xl text-center text-gray-600">
        o valor é: R${{ parseInt(valorFinalPorPessoa).toFixed(2) }}
      </p>
    </div>
  </div>
</template>
