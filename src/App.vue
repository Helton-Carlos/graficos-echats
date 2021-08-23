<template>
 <div class="coluna">
  <Tabela />
  <Tabela1 />
 </div>
</template>

<script>
import Tabela from "./components/Tabela.vue";
import Tabela1 from "./components/Tabela1.vue";

export default {
  name: "App",
  components: {
    Tabela,
    Tabela1
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0px;
}
.coluna{display:flex;flex-direction: column;}
</style>
