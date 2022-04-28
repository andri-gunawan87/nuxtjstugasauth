<template>
  <div class="py-4">
    <div class="container">
      <div class="form">
          <form v-on:submit.prevent="submitForm">
              <div class="field control">
                  <label class="label">Nama</label>
                  <input class="input" type="text" placeholder="Masukkan Nama" v-model="form.name" />
              </div>
              <div class="field control">
                  <label class="label">Pesan</label>
                  <textarea class="textarea" placeholder="Masukkan Pesan" v-model="form.message" >
                      </textarea>
              </div>
              <div class="field control">
                  <label class="label">Prioritas</label>
                 <select class="input" v-model="form.priority">
                     <option value="">Tidak ada Prioritas</option>
                     <option value="High">Tinggi</option>
                     <option value="Low">Redah</option>
                 </select>
              </div>
              <div class="field control">
                  <input type="checkbox" v-model="form.agreement" />
                  <label class="label">Anda telah menyetujui</label>
              </div>
              <div class="field control">
                  <button class="button is-primary">Submit</button>
              </div>

          </form>
      </div>
    </div>
    <div></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tasks: [
        {
          title: "Task 1",
          description: "ini deskripsi",
          isDone: false,
        },
      ],
      isCreating: false,
      form: {
          name: "",
          message: "",
          priority: "",
          agrrement: false
      },

      priority: [
          { option: "Tidak ada proritas", value: ""},
          { option: "Rendah", value: "Low"},
          { option: "Tinggi", value: "High"},
      ],
      
    };
  },
  methods: {
    doSomething() {
      alert("`Nothing to see here~");
    },
    
  },
};
</script>
<style></style>
