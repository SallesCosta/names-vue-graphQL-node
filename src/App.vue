<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>NameGator</h1>
      <h6 class="text-secondary">Gerador de Nomes com Vue, GraphQL e Node</h6>
    </div>
    <div id="main">
      <DomainList />
    </div>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'font-awesome/css/font-awesome.css'
import DomainList from './components/DomainList.vue'

export default {
  name: 'App',
  components: {
    DomainList,
  },
}
</script>

<style>
#slogan {
  margin-top: 30px;
  margin-botton: 30px;
}

#main {
  background: #f1f1f1;
  padding-top: 30px;
  padding-botton: 90px;
}
</style>
