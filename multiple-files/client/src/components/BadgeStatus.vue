<template>
  <h6>
    <span class="badge badge-secondary">
      {{status}}
    </span>
  </h6>
</template>

<script>
  export default {
    name: "BadgeStatus",
    props: ['status']
  };
</script>


