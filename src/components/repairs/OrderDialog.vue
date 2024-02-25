<script setup lang="ts">
const isDialogOpen = ref(false)

const order = ref()

const openDialog = () => {
  const storedOrder = sessionStorage.getItem('order')
  if (storedOrder) {
    order.value = JSON.parse(storedOrder)
    isDialogOpen.value = true
  }
  else {
    console.error('No order found in storage')
  }
}

defineExpose({ openDialog })
</script>

<template>
  <VDialog v-model="isDialogOpen">
    <VCard
      v-if="order"
      class="mx-auto"
      width="800"
    >
      <VCardTitle class="mt-3 ms-1 d-flex justify-space-between align-center">
        <h6 class="text-h5">
          Order No: {{ order.orderNo }}
        </h6>
        <div class="d-flex align-center">
          <h6 class="text-body-2 me-3">
            Type of Service:
          </h6>
          <VRadioGroup
            v-model="order.serviceType"
            inline
          >
            <VRadio
              label="EM"
              value="EM"
            />
            <VRadio
              label="GJ"
              value="GJ"
            />
            <VRadio
              label="BP"
              value="BP"
            />
          </VRadioGroup>
        </div>
      </VCardTitle>
      <VCardText>
        <VRow class="mt-3">
          <VCol class="pa-3">
            <h6 class="text-h6 mb-5">
              Completed Parts
            </h6>
            <div class="d-flex gap-y-2 flex-column">
              <div
                v-for="part in order.parts"
                :key="part.name"
              >
                <Parts :part="part" />
              </div>
            </div>
          </VCol>
          <VDivider vertical />
          <VCol class="pa-3">
            <h6 class="text-h6 mb-5">
              Completed Parts
            </h6>
            <div class="d-flex gap-y-2 flex-column">
              <div
                v-for="part in order.parts"
                :key="part.name"
              >
                <Parts :part="part" />
              </div>
            </div>
          </VCol>
          <VDivider vertical />
          <VCol class="pa-3">
            <h6 class="text-h6 mb-5">
              Completed Parts
            </h6>
            <div class="d-flex gap-y-2 flex-column">
              <div
                v-for="part in order.parts"
                :key="part.name"
              >
                <Parts :part="part" />
              </div>
            </div>
          </VCol>
        </VRow>
      </VCardText>
    </VCard>
  </VDialog>
</template>
