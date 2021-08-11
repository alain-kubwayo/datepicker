<template>
  <div class="mx-4 my-4">
    <v-date-picker
      :value="value"
      :is-range="this.range"
      v-model="$data[range ? 'dateRange' : 'date']"
      :columns="this.range ? layout.columns : layoutSingle.columns"
      :is-expanded="layout.isExpanded"
      mode="date"
      color="orange"
      :locale="{
        id: 'de',
        firstDayOfWeek: 2,
        masks: { weekdays: 'WW' },
      }"
    >
      <!-- <template v-slot="{ inputValue, togglePopover }">
        <input
          :value="
            range ? `${inputValue.start} - ${inputValue.end}` : `${inputValue}`
          "
          class="'bg-red-600'"
          @click="togglePopover()"
        />
      </template> -->
    </v-date-picker>
  </div>
</template>

<script>
import Datepicker from "v-calendar/lib/components/date-picker.umd";
import moment from "moment";
export default {
  components: { "v-date-picker": Datepicker },
  props: {
    range: {
      type: Boolean,
      required: true,
    },
    label: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    valuerange: {
      type: Object,
      default: function () {
        return {
          start: moment().format("YYYY.MM.DD"),
          end: moment().format("YYYY.MM.DD"),
        };
      },
    },
    valuesingle: {
      type: String,
      default: moment().format("YYYY.MM.DD"),
    },
    disableddates: {
      type: Array,
      required: false,
    },
  },
  mounted() {},
  data() {
    return {
      isOpen: false,
      value: new Date(),
      date: this.valuesingle,
      dateRange: {
        start: this.valuerange?.start,
        end: this.valuerange?.end,
      },
      modelConfig: {
        type: "string",
        mask: "DD.MM.YYYY",
      },
      themeStyles: {
        verticalDivider: "not-in-month",
        headerTitle: "my-title",
      },
    };
  },

  computed: {
    layout() {
      return this.$screens({
        // Default layout for mobile
        default: {
          columns: 1,
          isExpanded: true,
        },
        // Override for large screens
        lg: {
          columns: 2,
          isExpanded: false,
        },
      });
    },
    layoutSingle() {
      return this.$screens({
        // Default layout for mobile
        default: {
          columns: 1,
          isExpanded: true,
        },
        // Override for large screens
        lg: {
          columns: 1,
          isExpanded: false,
        },
      });
    },
  },
};
</script>

<style scoped>
.vc-container {
  font-family: "Times New Roman", Arial, sans-serif;
  color: var(--gray-700);
  border: none;
  border-top: 1px solid gray;
  border-bottom: 1px solid gray;
  border-color: var(--gray-400);
  border-radius: 0px;
}

.vc-focusable {
  background-color: pink;
}

.vc-continer {
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;
  --text-xs: 12px;
  --text-sm: 14px;
  --text-base: 16px;
  --text-lg: 18px;
  --leading-snug: 1.375;
  --rounded: 0.25rem;
  --rounded-lg: 0.5rem;
  --rounded-full: 9999px;
  --shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1),
    0 4px 6px -2px rgba(0, 0, 0, 0.05);
  --shadow-inner: inset 0 2px 4px 0 rgba(0, 0, 0, 0.06);
  --slide-translate: 22px;
  --slide-duration: 0.15s;
  --slide-timing: ease;
  --day-content-transition-time: 0.13s ease-in;
  --weeknumber-offset: -34px;
  position: relative;
  display: inline-flex;
  width: max-content;
  height: max-content;
  font-family: BlinkMacSystemFont, -apple-system, Segoe UI, Roboto, Oxygen,
    Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, Helvetica, Arial,
    sans-serif;
  color: var(--gray-900);
  background-color: var(--white);
  border: 1px solid;
  border-color: var(--gray-400);
  border-radius: var(--rounded-lg);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-tap-highlight-color: transparent;
}
</style>
