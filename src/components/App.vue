<template>
  <div>
    <div v-for="day in days">{{ day  }}</div>
  </div>
</template>

<script type="text/javascript">
  export default {
    data() {
      return {
        month: 2,
        year: 2020
      };  
    },
    computed: {
      days() {
        let days = [];
        let currentDay = this.$moment(`${this.year}-${this.month}-1`, 'YYYY-M-D');
        do {
          days.push(currentDay);
          currentDay = this.$moment(currentDay).add(1, 'days');
        } while ((currentDay.month() + 1) === this.month);

        const MONDAY = 1;
        const SUNDAY = 0;

        currentDay = this.$moment(days[0]);
        if (currentDay.day() !== MONDAY) {
          do {
            currentDay = this.$moment(currentDay).subtract(1, 'days');
            days.unshift(currentDay);
          } while (currentDay.day() !== MONDAY)
        }

        currentDay = this.$moment(days[days.length - 1]);
        if (currentDay.day() !== SUNDAY) {
          do {
            currentDay = this.$moment(currentDay).add(1, 'days');
            days.push(currentDay);
          } while(currentDay.day() !== SUNDAY);
        }
        return days;
      }
    }
  }
</script>
