<script setup lang="ts">
import { cn } from '@/lib/utils'
import { Button } from '@/components/ui/button'

import type { DateRange } from 'reka-ui'
import { RangeCalendar } from '@/components/ui/range-calendar'

import {
  DateFormatter,
  type DateValue,
  getLocalTimeZone,
  today
} from '@internationalized/date'
import { Popover, PopoverContent, PopoverTrigger } from '@/components/ui/popover'
import { CalendarIcon } from 'lucide-vue-next'
import { type Ref, ref } from 'vue'

import VueTailwindDatepicker from "vue-tailwind-datepicker";

import FormCustom from '@/components/custom/FormCustom.vue';

const df = new DateFormatter('pt-BR', {
  day: '2-digit',
  month: '2-digit',
  year: 'numeric',
})

const dateValue = ref([]);
const formatter = ref({
  date: "DD/MM/YYYY",
  month: "MMM",
});

const customShortcuts = () => {
  return [
    {
      label: "Hoje",
      atClick: () => {
        return [new Date(), new Date()];
      },
    },
    {
      label: "Ontem",
      atClick: () => {
        const date = new Date();
        return [new Date(date.setDate(date.getDate() - 1)), date];
      },
    },
    {
      label: "15 dias",
      atClick: () => {
        const date = new Date();
        return [new Date(date.setDate(date.getDate() - 15)), new Date()];
      },
    },
    {
      label: "30 dias",
      atClick: () => {
        const date = new Date();
        return [new Date(date.setDate(date.getDate() - 30)), new Date()];
      },
    },
  ];
};

</script>
<template>
  <div class="flex flex-1 flex-col gap-4 p-4 pt-0">
    <div class="flex justify-between">
      <h1 class="font-bold text-3xl">Playground</h1>
      <div><vue-tailwind-datepicker :formatter="formatter" v-model="dateValue" :shortcuts="customShortcuts" as-single use-range/></div>
    </div>
    <div class="grid auto-rows-min gap-4 md:grid-cols-3">
      <div class="aspect-video rounded-xl bg-muted/50" />
      <div class="aspect-video rounded-xl bg-muted/50" />
      <div class="aspect-video rounded-xl bg-muted/50" />
    </div>
    <div class="min-h-[100vh] flex-1 rounded-xl bg-muted/50 md:min-h-min p-6">
      <FormCustom />
    </div>
  </div>
</template>