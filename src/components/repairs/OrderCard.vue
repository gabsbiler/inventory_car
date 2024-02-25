<script setup lang="ts">
const props = defineProps(['item'])
</script>

<template>
  <VCard :title="`Repair No. ${item.orderNo}`">
    <VCardText>
      <div>
        Parts Pending: 123
      </div>
      <div>
        Parts Arrived: 123
      </div>
      <div>
        Parts Completed: 123
      </div>
    </VCardText>
    <VCardActions class="ma-1">
      <VBtn icon="ri-delete-bin-line" />
    </VCardActions>
  </VCard>
</template>
