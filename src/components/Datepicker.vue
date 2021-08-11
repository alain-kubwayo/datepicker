<template>
  <div>
    <v-date-picker
      :is-range="this.range"
      v-model="$data[range ? 'dateRange' : 'date']"
      :columns="this.range ? layout.columns : layoutSingle.columns"
      :is-expanded="layout.isExpanded"
      mode="date"
      color="orange"
      :locale="{ id: 'de', firstDayOfWeek: 2, masks: { weekdays: 'WW' } }"
      :disabled-dates="disableddates"
      :model-config="modelConfig"
    >
      <template v-slot="{ inputValue, togglePopover }"
        ><div class="relative m-2">
          <input
            :name="name"
            :value="
              range
                ? `${inputValue.start} - ${inputValue.end}`
                : `${inputValue}`
            "
            class="
              '
              border border-gray-400
              focus:border-gray-500
              appearance-none
              py-2
              rounded-lg
              bg-white
              outline-none
              text-md
              w-full
              md:w-1/6
              text-center
              '
            "
            @click="togglePopover()"
          />
          <span
            class="
              absolute
              left-2
              transform
              -translate-y-1/2
              transition
              duration-700
              bg-white
              px-2
            "
            >{{ label }}</span
          >
        </div>
      </template>
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
      // attributes: [
      //   {
      //     dates: {
      //       start: new Date(2021, 7, 10),
      //       end: new Date(2021, 7, 15),
      //     },
      //   },
      // ],
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

.vc-weekday {
  text-align: right;
  color: var(--gray-900);
  font-size: var(--text-sm);
  font-weight: var(--font-bold);
  line-height: 14px;
  padding-top: 4px;
  padding-bottom: 8px;
  cursor: default;
  -webkit-user-select: none;
  user-select: none;
}
</style>
