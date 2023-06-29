<template>
  <div
    class="flex justify-center h-screen bg-gradient-to-r from-green-500 to-green-400"
  >
    <div class="flex flex-col items-center justify-center pt-11">
      <div class="flex">
        <h1 class="text-4xl font-bold text-white p-8">Calculadora</h1>
        <img src="../assets/vue-logo.svg" width="52" alt="logo" />
      </div>

      <div>
        <p class="flex justify-end bg-white text-gray-500 p-2">
          {{ pegarOperacao }}
        </p>

        <p class="flex justify-end items-center bg-white w-48 h-12 p-2">
          {{ pegarResultado }}
        </p>
      </div>
      <div class="grid grid-cols-4">
        <button
          class="col-span-2 bg-white hover:bg-gray-300 border border-black-900"
          @click="ac"
        >
          AC
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="del"
        >
          DEL
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('÷')"
        >
          ÷
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('1')"
        >
          1
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('2')"
        >
          2
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('3')"
        >
          3
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('*')"
        >
          *
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('4')"
        >
          4
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('5')"
        >
          5
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('6')"
        >
          6
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('+')"
        >
          +
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('7')"
        >
          7
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('8')"
        >
          8
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('9')"
        >
          9
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('-')"
        >
          -
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('.')"
        >
          .
        </button>
        <button
          class="bg-white h-12 w-12 hover:bg-gray-300 border border-black-900"
          @click="click('0')"
        >
          0
        </button>
        <button
          class="col-span-2 bg-white hover:bg-gray-300 border border-black-900"
          @click="result"
        >
          =
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pegarOperacao: "",
      pegarResultado: "",
    };
  },
  methods: {
    click(par) {
      this.pegarResultado += par;
    },
    ac() {
      this.pegarResultado = "";
      this.pegarOperacao = "";
    },
    del() {
      if (this.pegarResultado.length >= 1) {
        this.pegarResultado = this.pegarResultado.substring(
          0,
          this.pegarResultado.length - 1
        );
      } else {
        this.pegarResultado = "0";
      }
    },
    result() {
      let operation = this.pegarResultado;
      this.pegarOperacao = operation;

      operation = operation.replace("x", "*");
      operation = operation.replace("÷", "/");
      this.pegarResultado = eval(operation);
    },
  },
};
</script>

<style></style>
