<script setup lang="ts">
const props = defineProps(['part'])
</script>

<template>
  <div class="d-flex gap-y-1 flex-column">
    <VCard>
      <VCardText class="d-flex gap-x-3">
        <div>
          <b>{{ props.part.name }}</b>
          <h6 class="text-body-2">
            Part No: {{ props.part.partNo }}
          </h6>
        </div>

        <div class="d-flex flex-column justify-center">
          <VBtn
            icon="ri-check-fill"
            density="compact"
            variant="text"
          />
          <VBtn
            icon="ri-arrow-right-s-line"
            density="compact"
            variant="text"
          />
        </div>
      </VCardText>
    </VCard>
  </div>
</template>
