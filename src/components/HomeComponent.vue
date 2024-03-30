<script setup>
import LayoutComponent from '@/components/LayoutComponent.vue';
import HeaderComponent from '@/components/HeaderComponent.vue';
import MovementsComponent from '@/components/MovementsComponent.vue';
import ResumeComponent from '@/components/Resume/ResumeComponent.vue';
</script>
<template>
  <LayoutComponent>
    <template #header>
      <HeaderComponent />
    </template>
    <template #resume>
      <ResumeComponent />
    </template>
    <template #movements>
      <MovementsComponent />
    </template>
  </LayoutComponent>
</template>
