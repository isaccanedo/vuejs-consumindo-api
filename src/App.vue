<template>
  <div id="app">
    <p>
   <div class="container">
     <h2>Lista</h2> {{hoje}}
     <div class="todo-form form-group">
       <div class="form-group-list">
       </div>
     </div>
   </div>
<div class="container">
  <h4>Resultado da API 1</h4>
   <table class="table table-dark">
    <tr>
      <td>ID</td>
      <td>Cargo</td>
      <td>Local</td>
      <td>Contrato</td>
      <td>Salário</td> 
    </tr>

   <tr v-for="resultado in resultados" v-bind:key="resultado.id">
      <td>{{resultado.id}}</td>
      <td>{{resultado.cargo}}</td>
      <td>{{resultado.local}}</td>
      <td>{{resultado.contrato}}</td>
      <td>{{resultado.salario}}</td>
   </tr>          

        </table>
</div>

<div class="container">
  <h4>Resultado da API 2</h4>
   <table class="table table-dark">    

    <tr>
      <td>ID</td>
      <td>Nome</td>
      <td>Sobrenome</td>
      <td>Endereço</td>
      <td>Cidade</td>  
    </tr> 

   <tr v-for="resultado2 in resultados2" v-bind:key="resultado2.id">
      <td>{{resultado2.id}}</td>
      <td>{{resultado2.nome}}</td>
      <td>{{resultado2.sobrenome}}</td>
      <td>{{resultado2.endereco}}</td>
      <td>{{resultado2.cidade}}</td>
   </tr>          

        </table>

</div>

<div class="container">
 <h4>Resultado da API 3</h4>
   <table class="table table-dark">
    <tr>
      <td>ID</td>
      <td>Endereço</td>
      <td>Bairro</td>
      <td>Cidade</td>
      <td>Estado</td>
    </tr> 

   <tr v-for="resultado3 in resultados3" v-bind:key="resultado3.id">
      <td>{{resultado3.id}}</td>
      <td>{{resultado3.endereco}}</td>
      <td>{{resultado3.bairro}}</td>
      <td>{{resultado3.cidade}}</td>
      <td>{{resultado3.estado}}</td>
   </tr>           

        </table>

</div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
name: 'app',
data: function() {
  return {
    dias: ['Domingo', 'Segunda', 'Terça', 'Quarta', 'Quinta', 'Sexta', 'Sábado'],
    meses: ['Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio', 'Junho', 'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'],
    resultados: [],
    resultados2: [],
    resultados3: []
  }

},

computed: {
  hoje: function() {
    let novaData = new Date()
    return `${this.dias[novaData.getDay()]}, ${novaData.getDate()} de ${this.meses[novaData.getMonth()]} de ${novaData.getFullYear()}`
  }
},
async created() {
const endPont1 = await axios.get("http://localhost:3345/vagas/listar")
this.resultados = endPont1.data;

}
}
</script>

<style>

</style>