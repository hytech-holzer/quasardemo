<template>
  <q-page padding>
    <!-- content -->

    <q-table
      title="Characters"
      :rows="rows"
      :columns="columns"
      row-key="name"
    />

  </q-page>
</template>

<script>


import axios from 'axios';
export default {
  async created() {
    console.log('created.');
    var url = 'https://www.breakingbadapi.com/api/characters/';
    await this.$axios.get(url).then(response => {
      this.rows = response.data;
    })

    this.columns = [
  {
    name: 'name',
    required: true,
    label: 'Name',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'birthday', align: 'left', label: 'Birthday', field: 'birthday', sortable: true },
  { name: 'calories', align: 'left', label: 'Nickname', field: 'nickname', sortable: true }
  ];
    console.log(this.rows);
  }, 
  
  data () {
    return {
      rows: [],
      columns: [],
      characters: ''
    }
  }
}
</script>
