<template>
  <div class="card mt-3">
    <div class="card-body">
      <div class="card-title"> {{ item.title }} </div>
      <BadgeStatus :status=" item.completed ? 'done' : 'doing' "></BadgeStatus>
    </div>
  </div>
</template>

<script>
  import BadgeStatus from './BadgeStatus';

  export default {
    name: "ListTodo",
    props: ["item"],
    components: { BadgeStatus }
  };
</script>