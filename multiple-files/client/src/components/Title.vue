<template>
  <div class="container text-center">
    <h2>
      {{ item }}
    </h2>
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "Title",
    props: ["item"]
  };
</script>