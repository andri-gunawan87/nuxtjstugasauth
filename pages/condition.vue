<template>
  <div>
    <div>
      <h1 v-if="num == 0">Angkanya 0</h1>
      <h1 v-if="num > 0">Angkanya Positif</h1>
      <h1 v-if="num < 0">Angkanya Negatif</h1>
      <h1 v-else>Bukan Angka 1</h1>
    </div>
    <div v-if="ok">
      <label>Username</label>
      <input placeholder="Enter Username" key="username" />
    </div>
    <div v-else>
      <label>Email</label>
      <input placeholder="Enter Email" key="username" />
    </div>
    <div>
      <button @click="ok = !ok">Toogle ok</button>
    </div>
    <!-- <div>
      <input placeholder="Enter Username" key="satu" value="{{satu}}"/>
      <input placeholder="Enter Username" key="dua" value="{{dua}}"/>
      {{pesan}}
    </div> -->
  </div>
</template>
<script>
export default {
  data() {
    return {
      num: -1,
      ok: true,
      satu: 1,
      dua: 2,
      pesan: 0,
    };
  },
};
</script>
