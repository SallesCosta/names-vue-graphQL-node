<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>NameGator</h1>
      <h6 class="text-secondary">Gerador de Nomes com Vue, GraphQL e Node</h6>
    </div>
    <div id="main">
      <div id="container">
        <div class="row">
          <div class="col-md">
            <h5>
              Prefixos<span class="badge-light">{{ prefixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="prefix in prefixes"
                    v-bind:key="prefix"
                  >
                    {{ prefix }}
                  </li>
                </ul>
                <input
                  clas="form-control"
                  type="text"
                  placeholder="digite o prefixo"
                />
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              Sufixos<span class="badge-info">{{ sufixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="sufix in sufixes"
                    v-bind:key="sufix"
                  >
                    {{ sufix }}
                  </li>
                </ul>
                <input
                  clas="form-control"
                  type="text"
                  placeholder="digite o sufixo"
                />
              </div>
            </div>
          </div>
        </div>
        <br />
        <h5>Dominios <span class="badge-info">{{domains.length}}</span></h5>
        <div class="card">
          <div class="card-body">
            <ul class='list-group' v-for="domain in domains" v-bind:key="domain">
              <li class='list-group-item'>{{ domain }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'font-awesome/css/font-awesome.css'

export default {
  name: 'App',
  data: function () {
    return {
      prefixes: ['Air', 'Jet', 'Flight'],
      sufixes: ['Hub', 'Station', 'Mart'],
      domains: [
        'AirHub',
        'AirStation',
        'AirMart',
        'JetHub',
        'JetStation',
        'JetMart',
        'FlightHub',
        'FlightStation',
        'FlightMart',
      ],
    }
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
