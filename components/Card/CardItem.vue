<template>

  <div
    v-if="!ss || !task.isDone"
    :class="[
      'item-task d-flex align-items-start border-bottom pt-3 pb-4',
      isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
      
    ]"
  >
    <input
      type="checkbox"
      name="status"
      id="task"
      class="me-2 mt-2"
      :checked="task.isDone"
      v-model="task.isDone"
    />
    <div
      v-if="!task.isDone"
      :class="[
        'd-flex flex-column',
        task.isDone ? 'text-decoration-line-through fst-italic' : '',
      ]"
    >
      <div class="title-task mb-1">
        <nuxt-link class="title-task mb-1" :to="'app/detail/' + task.id" >
{{ task.title }}
</nuxt-link>
      </div>
      <div class="description-task small text-muted">
        {{ task.description }}
      </div>
      <input class="form-control form-control-sm" type="date" />
    </div>
    <span v-else>Task Selesai</span>
  </div>
</template>
<script>
export default {
  // name: 'CardItem',
  props: {
    task: {
      type: Object,
      default: "Untitled",
    },
    isGrid: {
      type: Boolean,
      required: true,
      default: false,
    },
    ss: {
      type: Boolean,
      required: true,
      default: true,
    },
  },
  
};
</script>
