<template>
  <div>
    <date-picker
      v-model="date"
      :inline="true"
      range
      :open="false"
    ></date-picker>
    <button @click="stylePicker">Change Styles</button>
  </div>
</template>

<script>
import DatePicker from "vue2-datepicker";
import "vue2-datepicker/index.css";

export default {
  components: {
    DatePicker,
  },
  mounted() {},
  data() {
    return {
      date: new Date(),
    };
  },
  methods: {
    stylePicker() {
      const activeElements = document.querySelectorAll(".active");
      activeElements.forEach((elt) => {
        elt.style.backgroundColor = "red";
        elt.style.borderRadius = "5px 10px 15px 20px";
        console.log(elt);
      });
      const inRangeDates = document.querySelectorAll(".in-range");
      inRangeDates.forEach((elt) => {
        elt.style.background = "#333";
      });
    },
  },
};
</script>

<style scoped>
.active {
  background-color: red;
  border-radius: 10px;
}
.cell {
  color: green;
}
</style>
