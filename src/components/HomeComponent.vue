<script setup>
import { ref } from 'vue';
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
  },
  {
    id: 2,
    title: 'Movimiento 1',
    description: 'Deposito de honorarios',
    amount: 500,
  },
  {
    id: 3,
    title: 'Movimiento 3',
    description: 'Comida',
    amount: -100,
  },
  {
    id: 4,
    title: 'Movimiento 4',
    description: 'Colegiatura',
    amount: 1000,
  },
  {
    id: 5,
    title: 'Movimiento 5',
    description: 'Reparación equipo',
    amount: 1000,
  },
  {
    id: 6,
    title: 'Movimiento 6',
    description: 'Compras repuestos',
    amount: -800,
  },
  {
    id: 7,
    title: 'Movimiento 7',
    description: 'Reparación auto',
    amount: -1420,
  },
]);

const amounts = ref([100, 200, 500, 200, -400, -600, -300, 0, 300, 500]);
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
          <ActionComponent />
        </template>
      </ResumeComponent>
    </template>
    <template #movements>
      <MovementsComponent :movements="movements" />
    </template>
  </LayoutComponent>
</template>
