<template>
  <div>
    <div class='main'>
      <div class='container'>
        <div class='row'>
          <div class='col-md'>
            <ItemList v-bind:items='prefixes' title='Prefixos' v-on:addItem='addPrefix' v-on:removeItem='removePrefix' />
          </div>
          <div class='col-md'>
            <ItemList v-bind:items='sufixes' title='Sufixos' v-on:addItem='addSufix' v-on:removeItem='removeSufix' />
          </div>
        </div>
      </div>
    </div>
    <br/>
    <div class='container'>
      <h5>Domains <span class='badge badge-info'>{{ domains.length }}</span></h5>
      <div class='card'>
        <div class='card-body'>
          <ul class='list-group'>
            <li class='list-group-item' v-for='domain in domains' v-bind:key='domain.name'>
              <div class='row'>
                <div class='col-md'>
                  {{ domain.name }}
                </div>
                <div class='col-md text-right'>
                  <a class='btn btn-info' target='_blank' v-bind:href='domain.checkout'><span class='fa fa-shopping-cart'/></a>
                </div>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import 'bootstrap/dist/css/bootstrap.css';
  import 'font-awesome/css/font-awesome.css';
  import ItemList from './ItemList';

  export default {
    name: 'app',
    components: {
      ItemList
    },
    data: function () {
      return {
        prefix: '',
        sufix: '',
        prefixes: ['Air', 'Jet', 'Flight'],
        sufixes: ['Hub', 'Station', 'Mart'],
      }
    },
    methods: {
      addPrefix(prefix) {
        prefix.length && 
          this.prefixes.push(prefix);
      },
      addSufix(sufix) {
        sufix.length && 
          this.sufixes.push(sufix);
      },
      removePrefix(prefix) {
        this.prefixes.splice(this.prefix.indexOf(prefix), 1);
      },
      removeSufix(sufix) {
        this.sufixes.splice(this.sufix.indexOf(sufix), 1);
      },
    },
    computed: {
      domains() {
        const domains = [];
        for(const prefix of this.prefixes) {
          for(const sufix of this.sufixes) {
            let name = prefix + sufix;
            let url = name.toLowerCase();
            let checkout = `https://checkout.hostgator.com.br/?a=add&sld=${url}&tld=.com`;
            domains.push({
              name,
              checkout
            });
          }
        }
        return domains;
      },
    }
  };

</script>
  
<style>
 
</style>
