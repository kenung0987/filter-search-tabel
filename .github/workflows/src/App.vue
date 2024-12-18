<template>
  <div>
    <h1>Filter Search Tabel NIK</h1>
    <input type="text" v-model="searchQuery" placeholder="Cari NIK...">
    <table border="1">
      <thead>
        <tr>
          <th>NIK</th>
          <th>Nama</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in filteredItems" :key="index">
          <td>{{ item.nik }}</td>
          <td>{{ item.nama }}</td>
          <td>{{ item.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { dataItems } from './data.js'

export default {
  data() {
    return {
      searchQuery: '',
      items: dataItems
    }
  },
  computed: {
    filteredItems() {
      return this.items.filter(item => {
        return item.nik.includes(this.searchQuery) ||
               item.nama.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
               item.email.toLowerCase().includes(this.searchQuery.toLowerCase())
      })
    }
  }
}
</script>
  
