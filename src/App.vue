<template>
  <div id="app">
    <date-picker
      :range="true"
      :name="'vacation_duration'"
      :label="'Zeitraum'"
      :valuerange="{ start: '2021.07.24', end: '2021.07.28' }"
      :disableddates="['2021.07.09', '2021.07.11']"
    ></date-picker>
    <date-picker
      :range="false"
      :name="'start_date'"
      :label="'Startdatum'"
      :valuesingle="'2021.07.27'"
      :disableddates="['2021.07.15']"
    ></date-picker>
    <test
      :range="true"
      :name="'vacation_duration'"
      :label="'Zeitraum'"
      :valuerange="{ start: '2021.07.24', end: '2021.07.28' }"
      :disableddates="['2021.07.09', '2021.07.11']"
    ></test>
    <test
      :range="false"
      :name="'start_date'"
      :label="'Startdatum'"
      :valuesingle="'2021.07.27'"
      :disableddates="['2021.07.09', '2021.07.11']"
    ></test>
  </div>
</template>

<script>
import DatePicker from "./components/Datepicker.vue";
import Test from "./components/Test.vue";
export default {
  name: "App",
  components: {
    DatePicker,
    Test,
  },
};
</script>

<style src="./assets/tailwind.css" /> 

