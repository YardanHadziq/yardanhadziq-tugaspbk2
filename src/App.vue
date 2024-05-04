<template>
  <div class="app-data">
    <form @submit.prevent="addName" class="form-data">
      <h1 class="judul" :style="{ color: 'white' }">Pendaftaran Data Nama</h1>
      <input type="text" v-model="newName" @keyup.enter="addName" placeholder="Masukkan nama" class="input-nama">
      <button type="submit" class="button-data">Tambah Nama</button>
    </form>
    <ul>
      <li v-for="(name, index) in names" :key="index" :class="{ 'completed': name.completed }">
        <span>{{ name }}</span>
        <button @click="removeName(index)">Hapus</button>
      </li>
    </ul>
    <div :class="{ 'empty': names.length === 0 }">
      Data nama anda akan muncul disini
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newName: '',
      names: []
    };
  },
  methods: {
    addName() {
      if (this.newName.trim() !== '') {
        this.names.push(this.newName);
        this.newName = '';
      }
    },
    removeName(index) {
      this.names.splice(index, 1);
    }
  }
};
</script>

<style>
  body {
    background: rgb(5,0,40);
    background: linear-gradient(90deg, rgba(5,0,40,1) 0%, rgba(34,69,91,1) 51%, rgba(29,137,157,1) 100%);
  }
  .app-data {
    background: rgba(0, 0, 0, 0.35);
    border-radius: 20px;
    padding: 45px;
  }
  .empty {
  color: red;
  font-weight: bold;
  }
</style>
