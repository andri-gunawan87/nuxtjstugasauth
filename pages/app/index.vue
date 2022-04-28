<template>
  <div class="py-4">
    <div v-if="isLoading"><p class="text-center">Loading</p>
    </div>
    <div v-else-if="!isAuthenticated"><p class="text-center">Silahkan login untuk melihat data</p>
    </div>
    <div class="container" v-else>
      <div
        class="
          title
          border-bottom
          d-flex
          align-items-center
          justify-content-between
          py-2
        "
      >
        <h5>Task</h5>
        <div>
          <select @change="sortBy($event)" v-model="sort">
            <option value="">SortBy</option>
            <option value="asc">Ascending</option>
            <option value="desc">Descending</option>
          </select>
        </div>

        <div>
          <select v-model="kategori">
            <option value="">Semua Prioritas</option>
            <option value="High">Penting</option>
            <option value="Mid">Tidak Penting</option>
            <option value="Low">Tidak Perlu</option>
          </select>
        </div>
        <button class="btn btn-outline-secondary py-1 px-3" @click="ss = !ss">
          {{ ss ? "Show" : "Hide" }}
        </button>
        <button class="btn btn-outline-primary py-1 px-3 me-4" @click="shuffle">
          Shuffle!
        </button>
        <div class="d-flex align-items-center">
          <input
            type="text"
            class="form-control"
            placeholder="Search"
            v-model="searchQuery"
          />
          <span class="me-2">View As</span>
          <button
            class="btn btn-outline-secondary py-1 px-3"
            @click="isGrid = !isGrid"
          >
            {{ isGrid ? "Grid" : "List" }}
          </button>
        </div>
      </div>

      <transition-group name="tasks" tag="div" class="list-task row">
        <CardItem
          v-for="tasks in resultQuery"
          :key="tasks.id"
          :task="tasks"
          :isGrid="isGrid"
          :ss="ss"
        />
      </transition-group>
      <div class="action py-2">
        <a
          href="#"
          class="add-button"
          v-if="!isCreating"
          @click="isCreating = !isCreating"
          >Add Task</a
        >
        <div class="add-card" v-else>
          <form v-on:submit.prevent="append">
            <div class="card mb-2">
              <div class="card-body d-flex flex-column p-0">
                <input
                  class="form-control border-0 mb-2"
                  placeholder="Title"
                  type="text"
                  v-model="form.title"
                />
                <textarea
                  class="form-control border-0 small"
                  placeholder="Description"
                  rows="3"
                  v-model="form.description"
                ></textarea>
              </div>
              <label class="label">Prioritas</label>
              <select class="input" v-model="form.kategori">
                <option value="">Tidak ada Prioritas</option>
                <option value="High">Penting</option>
                <option value="Mid">Tidak Penting</option>
                <option value="Low">Tidak Perlu</option>
              </select>

              <div class="field control">
                <input type="checkbox" v-model="form.isDone" />
                <label class="label">Apakah task ini sudah selesai?</label>
              </div>
            </div>
            <div class="button-wrapper d-flex">
              <button class="btn btn-primary me-2" type="submit">Save</button>
              <button
                class="btn btn-outline-secondary"
                @click="isCreating = !isCreating"
              >
                Cancel
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
    <div></div>
  </div>
</template>
<script>
import CardItem from "@/components/Card/CardItem.vue";
import { mapGetters } from "vuex";

export default {
  components: {
    CardItem,
  },
  data() {
    return {
      searchQuery: "",
      kategori: "",
      sort: "",
      tasks: [
        {
          id: 1,
          title: "Task 1",
          description: "ini deskripsi 1",
          isDone: false,
          ss: false,
          kategori: "Low",
        },
        {
          id: 2,
          title: "Task 2",
          description: "ini deskripsi 2",
          isDone: false,
          ss: false,
          kategori: "Mid",
        },
        {
          id: 3,
          title: "Task 3",
          description: " ini deskripsi 3",
          isDone: false,
          kategori: "Mid",
        },
        {
          id: 4,
          title: "Task 4",
          description: " ini deskripsi 4",
          isDone: false,
          kategori: "High",
        },
      ],
      form: {
        title: "",
        description: "",
        isDone: false,
        kategori: "Low",
      },
      isCreating: false,
      isGrid: false,
      ss: false,
      itemId: 0,
      isLoading: true,
    };
  },
  beforeCreate() {
      console.log("before created");
      // console.log(document.getElementById("life"));
    },
    created() {
      console.log("created");
      // console.log(document.getElementById("life"));
    },
    beforeMount() {
      console.log("beforeMount");
      // console.log(document.getElementById("life"));
    },
    mounted() {
      setTimeout(() => {
        this.isLoading = false;
      }, 1000);
    },
    beforeUpdate() {
      console.log("beforeUpdate");
      // console.log(document.getElementById("life").textContent);
    },
    updated() {
      console.log("Updated");
      // console.log(document.getElementById("life").textContent);
    },
  methods: {
    doSomething() {
      alert("`Nothing to see here~");
    },
    append() {
      this.tasks.push({
        id: this.itemId++,
        title: this.form.title,
        description: this.form.description,
        isDone: this.form.isDone,
        kategori: this.form.kategori,
      },
      this.form.title = "",
      this.form.description = "",
      this.form.isDone = false,
      this.form.kategori = "",
      );
    },
    shuffle() {
      this.tasks = _.shuffle(this.tasks);
    },
    sortBy(event) {
      this.tasks = _.orderBy(this.tasks, ["title"], [event.target.value]);
    },
  },
  computed: {
    ...mapGetters(["isAuthenticated", "loggedInUser"]),
    // resultQuery() {
    //   if (this.searchQuery) {
    //     return this.tasks.filter((item) => {
    //       return this.searchQuery
    //         .toLowerCase()
    //         .split(" ")
    //         .every((v) => item.title.toLowerCase().includes(v));
    //     });
    //   } else {
    //     console.log(this.tasks);
    //     return this.tasks;
    //   }
    // },
    resultQuery() {
      if (this.kategori) {
        return this.tasks.filter((item) => {
          return this.kategori
            .toLowerCase()
            .split(" ")
            .every((v) => item.kategori.toLowerCase().includes(v));
        });
      } else {
        console.log(this.tasks);
        return this.tasks;
      }
    },
    
  },
};
</script>
<style>
.tasks-move {
  transition: 0.4s;
}
</style>
