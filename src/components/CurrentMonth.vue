<template>
  <div>
    <div>{{ formattedDate  }}</div>
    <button @click="inc">+</button>
    <button @click="dec">-</button>
  </div>
</template>

<script type="text/javascript">
  export default {
    computed: {
      year() {
        return this.$store.state.currentYear;
      },
      month() {
        return this.$store.state.currentMonth;
      },
      formattedDate() {
        return this.$moment(`${this.year}-${this.month}-1`, 'YYYY-M-D').format('MMMM YYYY');
      }
    },
    methods: {
      inc() {

      },
      dec() {

      }
    }
  }
</script>