<template>
  <tr>
    <td>{{ row.mascota }}</td>
    <td>{{ row.seccion }}</td>
    <td>{{ row.familia }}</td>
    <td>{{ row.subfamilia }}</td>
    <td>{{ row.producto }}</td>
    <td>{{ row.coste }}</td>
    <td><input class="form-control" type="text" v-model="row.unidades" value="row.unidades" /></td>
    <td>{{ row.precio }}</td>
    <td>{{ costeTotal }}</td>
  </tr>
</template>

<script>
  export default {
    props: ['row'],
    data() {
      return {
        row: this.row,
        costeTotal: this.calculateCosteTotal()
      }
    },
    created() {
      this.$emit('add-to-total', this.row);
    },
    methods: {
      calculateCosteTotal: function() {
        return this.row.coste * this.row.unidades;
      }
    }
  }
</script>
