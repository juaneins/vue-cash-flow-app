<script setup>
import { ref } from 'vue';
import LayoutComponent from '@/components/LayoutComponent.vue';
import HeaderComponent from '@/components/HeaderComponent.vue';
import MovementsComponent from '@/components/MovementsComponent.vue';
import ResumeComponent from '@/components/Resume/ResumeComponent.vue';

const amount = ref(null);
</script>
<template>
  <LayoutComponent>
    <template #header>
      <HeaderComponent />
    </template>
    <template #resume>
      <ResumeComponent :label="'Ahorro Total'" :total-amount="12500" :amount="amount">
        <template #graphic>
          <div>graphic</div>
        </template>
        <template #action> action </template>
      </ResumeComponent>
    </template>
    <template #movements>
      <MovementsComponent />
    </template>
  </LayoutComponent>
</template>
