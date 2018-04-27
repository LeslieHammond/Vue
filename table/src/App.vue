<template>
  <div id="app">
    <table class="table">
      <thead>
        <tr>
          <th>Mascota</th>
          <th>Sección</th>
          <th>Familia</th>
          <th>Subfamilia</th>
          <th>Producto</th>
          <th>Coste</th>
          <th>Unidades</th>
          <th>Precio</th>
          <th>Coste Total</th>
        </tr>
      </thead>
      <tbody>
        <row
          v-for="(row, index) in rows"
          :key="index"
          :row="row"
          @add-to-total="addToTotal"
        />
        </row>
      </tbody>
      <tfoot>
        <tr>
          <th colspan="5" class="text-right">Total:</th>
          <th>{{ total.coste }}</th>
          <th>{{ total.unidades }}</th>
          <th>{{ total.precio }}</th>
          <th>-</th>
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>
  import Row from './components/Row.vue'

  export default {
    name: 'app',
    data() {
      return {
        rows: JSON.parse(json),
        total: {
          coste: 0,
          unidades: 0,
          precio: 0,
        }
      }
    },
    components: {
      Row
    },
    methods: {
      addToTotal: function (row) {
        this.total.coste += parseFloat(row.coste * row.unidades);
        this.total.precio += parseFloat(row.precio * row.unidades);
        this.total.unidades += parseInt(row.unidades);
      }
    }
  }
</script>
