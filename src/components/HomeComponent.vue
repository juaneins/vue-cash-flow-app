<script setup>
import { ref, computed } from 'vue';
import LayoutComponent from '@/components/LayoutComponent.vue';
import HeaderComponent from '@/components/HeaderComponent.vue';
import MovementsComponent from '@/components/Movements/MovementsComponent.vue';
import ResumeComponent from '@/components/Resume/ResumeComponent.vue';
import ActionComponent from '@/components/ActionComponent.vue';
import GraphicComponent from '@/components/Resume/GraphicComponent.vue';
const amount = ref(null);

const movements = ref([
  {
    id: 1,
    title: 'Movimiento',
    description: 'Deposito de salario',
    amount: 1000,
    time: new Date('03/05/2024'),
  },
  {
    id: 2,
    title: 'Movimiento 1',
    description: 'Gasto de honorarios',
    amount: -500,
    time: new Date('04/01/2024'),
  },
  {
    id: 3,
    title: 'Movimiento 3',
    description: 'Comida',
    amount: -700,
    time: new Date('01/01/2024'),
  },
  {
    id: 4,
    title: 'Movimiento 4',
    description: 'Colegiatura',
    amount: -1800,
    time: new Date('03/15/2024'),
  },
  {
    id: 5,
    title: 'Movimiento 5',
    description: 'Reparación equipo',
    amount: 1000,
    time: new Date('03/25/2024'),
  },
  {
    id: 6,
    title: 'Movimiento 6',
    description: 'Compras repuestos',
    amount: -800,
    time: new Date('03/08/2024'),
  },
  {
    id: 7,
    title: 'Movimiento 7',
    description: 'Reparación auto',
    amount: -1420,
    time: new Date('04/01/2024'),
  },
]);

const amounts = computed(() => {
  const lastDays = movements.value
    .filter((m) => {
      const today = new Date();
      const oldDate = today.setDate(today.getDate() - 30);
      return m.time > oldDate;
    })
    .map((m) => m.amount);

  return lastDays.map((m, i) => {
    const lastMovements = lastDays.slice(0, i);
    return lastMovements.reduce((suma, movement) => {
      return suma + movement;
    }, 0);
  });
});

const create = (movement) => {
  movements.value.push(movement);
};

const remove = (id) => {
  const index = movements.value.findIndex((m) => m.id === id);
  movements.value.splice(index, 1);
  console.log(movements);
};
</script>
<template>
  <LayoutComponent>
    <template #header>
      <HeaderComponent />
    </template>
    <template #resume>
      <ResumeComponent :label="'Ahorro Total'" :total-amount="12500" :amount="amount">
        <template #graphic>
          <GraphicComponent :amounts="amounts" />
        </template>
        <template #action>
          <ActionComponent @create="create" />
        </template>
      </ResumeComponent>
    </template>
    <template #movements>
      <MovementsComponent :movements="movements" @remove="remove" />
    </template>
  </LayoutComponent>
</template>
