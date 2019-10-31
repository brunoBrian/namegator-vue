<template>
  <div>
    <div id='slogan' class='text-center'>
      <h1>NameGator</h1>
      <br/>
      <h2 class='text-secondary'>Gerador de Nomes utilizando Vue.js, GraphQl e NodeJs</h2>
    </div>
    <div class='main'>
      <DomainList />
    </div>
  </div>
</template>

<script>
  import 'bootstrap/dist/css/bootstrap.css';
  import 'font-awesome/css/font-awesome.css';
  import DomainList from './components/DomainList';

  export default {
    name: 'app',
    components: {
      DomainList
    }
  };

</script>
  
<style>
  #slogan {
    margin: 30px 0;
  }

  #main {
    background-color: #f1f1f1;
    padding: 30px;
  }
</style>
