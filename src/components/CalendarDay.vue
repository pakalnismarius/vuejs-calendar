<template>
  <div class="day">{{ day.format('D') }}</div>
</template>

<script type="text/javascript">
  export default {
    props: [ "day" ]
  }
</script>