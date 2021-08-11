<template>
  <div id="app">
    <v-calendar
      value="date"
      title-position="right"
      :formats="forDatePicker"
      :attributes="action"
    ></v-calendar>
    <v-date-picker
      mode="single"
      :attributes="action"
      v-model="action[0].dates"
      :formats="forDatePicker"
    ></v-date-picker>
  </div>
</template>

<script>
import Vue from "vue";
import VCalendar from "v-calendar";
// import "v-calendar/lib/v-calendar.min.css";
Vue.use(VCalendar, {
  firstDayOfWeek: 2,
  locale: "en-US",
  titleTransition: "slide-v",
  weeksTransition: "fade",
  datePickerTintColor: "#1ebb42",
  datePickerShowCaps: true,
});
export default {
  name: "app",
  data() {
    return {
      date: new Date(),
      options: {
        animated: !0,
        backgroundColor: "white",
        color: "black",
        height: "1.8rem",
        borderWidth: "4px",
        borderStyle: "solid",
        borderRadius: "5px",
        opacity: 1,
      },
      forDatePicker: {
        title: "MMM of YYYY",
        navMonths: "MMM",
        weekdays: "WWW",
        input: ["YYYY/MM/DD", "YYYY/MM/D", "YYYY-MM-DD"],
        dayPopover: "Do of MMMM",
        data: ["YYYY-MM-DD", "YYYY/MM/DD"],
      },
      action: [
        {
          key: "today",
          highlight: {
            backgroundColor: "#000000",
            borderRadius: "5px",
            borderColor: "#1ebb42",
            borderWidth: "4px",
          },
          contentStyle: {
            color: "#fff",
            borderWidth: "4px",
            borderRadius: "5px",
          },
          dates: [new Date("2018/10/17"), new Date(), new Date("2018/10/21")],
        },
      ],
    };
  },
  created() {
    console.log(this.action[0].dates);
  },
};
</script>