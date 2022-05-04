<script setup lang="ts">
import MediumCommentComponent from "./MediumCommentComponent.vue";
import MediumCommentComponentSkeleton from "./MediumCommentComponentSkeleton.vue";
</script>
<template>
  <Suspense>
    <template #default>
      <MediumCommentComponent />
    </template>
    <template #fallback>
      <MediumCommentComponentSkeleton />
    </template>
  </Suspense>
</template>
