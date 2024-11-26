<script setup>
import { ref, computed } from "vue";

const employees = ref([]);

const name = ref('');
const date = ref('');
const daysWorked = ref(1);
const salary = ref(0);

const addEmployee = () => {
  if (name.value && date.value && daysWorked.value > 0 && salary.value > 0) {
    employees.value.push({
      id: Date.now(),
      name: name.value,
      date: date.value,
      daysWorked: daysWorked.value,
      salary: salary.value,
    });
    name.value = '';
    date.value = '';
    daysWorked.value = 1;
    salary.value = 0;
  }
};


const removeEmployee = (id) => {
  employees.value = employees.value.filter((employee) => employee.id !== id);
};

const totalWithoutTaxes = computed(() => {
  return employees.value.reduce((sum, emp) => sum + Number(emp.salary), 0);
});
const totalWithTaxes = computed(() => {
  return totalWithoutTaxes.value * 0.85;
});
</script>

<template>
  
</template>

<style scoped>

</style>
