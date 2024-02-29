<style>
.biru {
  color: blue;
}

.font-size {
  font-size: 50px;
}
</style>
<template>
  {{ nama }}
  <h1 class="biru">pesat</h1>
  <h1 v-bind="objectProperty" v-if="tampilkan">{{ nama }}</h1>
  <button v-show="tampilkanButton">button</button>
  <p>-----------------counter-------------------------</p>
  <button @click="counter">tambah</button>
  {{ count }}
  <p>------------class binding-----------------</p>

  <h1 class="biru" :class="{ 'font-size': fontBig }">pembangunan satu</h1>
  <button @click="rubah">click</button>

  <p>--------------------list rendering--------------</p>
  <!-- <ul>
    <li v-for="siswa in dataKelas">{{ siswa.nama }}</li>
  </ul> -->
  <label for="nama">nama</label>
  <input type="text" v-model="formData.nama">
  <br>
  <br>
  <label for="nama">kelas</label>
  <input type="text" v-model="formData.kelas">
  <br>
  <br>
  <button @click="tambahData">tambah</button>

  <br>
  <table border="1" cellpadding="10">
    <tr>
      <th>Id</th>
      <th>Unique Id</th>
      <th>Nama</th>
      <th>Kelas</th>
      <th>Aksi</th>
    </tr>
    <tr v-for="(siswa, index) in dataKelas">
      <td>{{ index + 1 }}</td>
      <td>{{ siswa.id }}</td>
      <td>{{ siswa.nama }}</td>
      <td>{{ siswa.kelas }}</td>
      <td><button @click="hapus(siswa.id)">hapus</button></td>
    </tr>
  </table>
</template>
<script>
export default {
  data() {
    return {
      formData: {
        nama: '',
        kelas: ''
      },
      count: 0,
      nama: 'zaenal',
      objectProperty: {
        class: 'biru',
      },
      tampilkan: false,
      tampilkanButton: false,
      fontBig: false,
      dataKelas: []
    }
  },
  methods: {
    counter() {
      this.count = this.count + 1
    },
    rubah() {
      if (this.fontBig) {
        this.fontBig = false;
      } else {
        this.fontBig = true;
      }

    },
    tambahData() {
      //  alert(this.formData.nama)
      this.dataKelas.push({
        id:Date.now(),
        nama: this.formData.nama,
        kelas: this.formData.kelas
      });
      
      this.formData={
        nama:'',
        kelas:''
      }
    },
    hapus(id){
      this.dataKelas=
      this.dataKelas.filter(item=>item.id != id);
    }
  }
}
</script>