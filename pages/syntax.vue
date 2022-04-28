<template>
  <div class="py-4">
    <div class="container">
      <div class="title border-bottom red">
        <h5>Task</h5>
      </div>
      <div class="list-task">
        <div
          class="item-task d-flex align-items-center border-bottom pt-3 pb-4"
        >
          <input type="checkbox" name="status" id="task" class="me-2" />
          <div class="title-task">Tugas 1</div>
        </div>
      </div>
      <div class="action py-2">
        <a href="#" class="add-button">Add Task</a>
      </div>
      {{ masg }}<br />
      {{ pro }}<br />
      <span>
        <p>Menggunakan kurung kurawal: {{ rawHtml }}</p>
        <p>Menggunakan v-html directive: <span v-html="rawHtml"></span></p>
        <button v-bind:disabled="isButtonDisabled">Button</button>
      </span>
      {{ number + 1 }}<br />
      {{ ok ? "YES" : "NO" }}<br />
      {{ message.split("").reverse().join("") }}<br />
      <div v-bind:id="'list-' + id"></div>
      <p v-if="seen">Now you see me</p>
      <p v-if="!seen">seen is {{ seen }}</p>
      <a v-bind:href="url"> click Me</a><br />
      <a v-on:click="doSomething"> Do Something </a>
      <a v-bind:[attributeName]="url"> attributeName </a>
      <a v-on:[eventName]="doSomething"> ... </a>

      <hr />
      <!-- full syntax -->
      <a v-bind:href="url"> Link Baru </a><br />
      <!-- shorthand -->
      <a :href="url"> Link Baru </a><br />
      <!-- shorthand dengan argumen dinamis (2.6.0+) -->
      <a :[key]="url"> Link Baru </a><br />

      <hr />
      <!-- full syntax -->
      <a v-on:click="doSomething"> doSomething </a><br />
      <!-- shorthand -->
      <a @click="doSomething"> doSomething </a><br />
      <!-- shorthand dengan argumen dinamis (2.6.0+) -->
      <a @[event]="doSomething"> doSomething </a><br />
    </div>
    <hr />

    <h1>Styling</h1>
    <div v-bind:class="{ active: isActive, 'text-danger': hasError }">
      Style
    </div>
    <div :class="{ active: isActive }">Style</div>
    <div v-bind:class="classObject">classObject</div>
    <div v-bind:class="[activeClass, errorClass]"></div>

    <div v-bind:class="[isActive ? activeClass : '', errorClass]">ternanry</div>
    <div v-bind:class="[{ active: isActive }, errorClass]">ternanry</div>

    <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }">
      Binding inline styles
    </div>

    <div v-bind:style="styleObject">objek style secara langsung</div>
    <div v-bind:style="{ color: ['red', 'yellow', 'blue'] }">Stye Object</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      masg: "Rabu Sore",
      pro: "data-data ngga penting",
      rawHtml:
        '<p>Menggunakan v-html directive: <span v-html="rawHtml"></span></p>',
      isButtonDisabled: true,
      number: 23,
      ok: true,
      id: 12,
      message: "banyak yang tidak tahu",
      seen: true,
      url: "https://sekolahbeta.alkademi.id/",
      attributeName: "href",
      eventName: "Click",
      isActive: true,
      hasError: true,
      classObject: {
        active: true,
        "text-success": true,
      },
      activeClass: "active",
      errorClass: "text-danger",
      activeColor: "red",
      fontSize: 30,
      styleObject: {
        color: "red",
        fontSize: "13px",
      },
    };
  },
  methods: {
    doSomething() {
      alert("`Nothing to see here~");
    },
  },
};
</script>
<style>
.red {
  color: blue;
}
.active {
  background: yellow;
}
</style>
