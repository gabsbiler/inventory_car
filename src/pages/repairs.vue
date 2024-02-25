<script setup lang="ts">
const OrderDialogRef = ref(null)

const orders = ref([
  {
    orderNo: 32415329,
    serviceType: 'EM',
    parts: [
      {
        name: 'AxleTech Brakes for Honda Civic 2022',
        partNo: 66145344,
        status: 'completed',
      },
      {
        name: 'AxleTech Brakes for Honda Civic 2022',
        partNo: 66145345,
        status: 'waiting',
      },
      {
        name: 'AxleTech Brakes for Honda Civic 2022',
        partNo: 66145346,
        status: 'arrived',
      },
    ],
  },
  {
    orderNo: 32415330,
    serviceType: 'GJ',
    parts: [
      {
        name: 'Quantum Headlights for Toyota Corolla 2021',
        partNo: 67145347,
        status: 'waiting',
      },
      {
        name: 'Quantum Headlights for Toyota Corolla 2021',
        partNo: 67145348,
        status: 'completed',
      },
      {
        name: 'Quantum Headlights for Toyota Corolla 2021',
        partNo: 67145349,
        status: 'arrived',
      },
    ],
  },
  {
    orderNo: 32415331,
    serviceType: 'BP',
    parts: [
      {
        name: 'TurboCharge Kit for Subaru WRX 2023',
        partNo: 68145350,
        status: 'arrived',
      },
      {
        name: 'TurboCharge Kit for Subaru WRX 2023',
        partNo: 68145351,
        status: 'waiting',
      },
      {
        name: 'TurboCharge Kit for Subaru WRX 2023',
        partNo: 68145352,
        status: 'completed',
      },
    ],
  },
  {
    orderNo: 32415332,
    serviceType: 'EM',
    parts: [
      {
        name: 'Falcon Shocks for Jeep Wrangler 2024',
        partNo: 69145353,
        status: 'completed',
      },
      {
        name: 'Falcon Shocks for Jeep Wrangler 2024',
        partNo: 69145354,
        status: 'waiting',
      },
      {
        name: 'Falcon Shocks for Jeep Wrangler 2024',
        partNo: 69145355,
        status: 'arrived',
      },
    ],
  },
  {
    orderNo: 32415333,
    serviceType: 'GJ',
    parts: [
      {
        name: 'Velocity Air Filter for Ford Mustang 2022',
        partNo: 70145356,
        status: 'waiting',
      },
      {
        name: 'Velocity Air Filter for Ford Mustang 2022',
        partNo: 70145357,
        status: 'arrived',
      },
      {
        name: 'Velocity Air Filter for Ford Mustang 2022',
        partNo: 70145358,
        status: 'completed',
      },
    ],
  },
  {
    orderNo: 32415329,
    serviceType: 'EM',
    parts: [
      {
        name: 'AxleTech Brakes for Honda Civic 2022',
        partNo: 66145344,
        status: 'completed',
      },
      {
        name: 'AxleTech Brakes for Honda Civic 2022',
        partNo: 66145345,
        status: 'waiting',
      },
      {
        name: 'AxleTech Brakes for Honda Civic 2022',
        partNo: 66145346,
        status: 'arrived',
      },
    ],
  },
  {
    orderNo: 32415330,
    serviceType: 'GJ',
    parts: [
      {
        name: 'Quantum Headlights for Toyota Corolla 2021',
        partNo: 67145347,
        status: 'waiting',
      },
      {
        name: 'Quantum Headlights for Toyota Corolla 2021',
        partNo: 67145348,
        status: 'completed',
      },
      {
        name: 'Quantum Headlights for Toyota Corolla 2021',
        partNo: 67145349,
        status: 'arrived',
      },
    ],
  },
  {
    orderNo: 32415331,
    serviceType: 'BP',
    parts: [
      {
        name: 'TurboCharge Kit for Subaru WRX 2023',
        partNo: 68145350,
        status: 'arrived',
      },
      {
        name: 'TurboCharge Kit for Subaru WRX 2023',
        partNo: 68145351,
        status: 'waiting',
      },
      {
        name: 'TurboCharge Kit for Subaru WRX 2023',
        partNo: 68145352,
        status: 'completed',
      },
    ],
  },
  {
    orderNo: 32415332,
    serviceType: 'EM',
    parts: [
      {
        name: 'Falcon Shocks for Jeep Wrangler 2024',
        partNo: 69145353,
        status: 'completed',
      },
      {
        name: 'Falcon Shocks for Jeep Wrangler 2024',
        partNo: 69145354,
        status: 'waiting',
      },
      {
        name: 'Falcon Shocks for Jeep Wrangler 2024',
        partNo: 69145355,
        status: 'arrived',
      },
    ],
  },
  {
    orderNo: 32415333,
    serviceType: 'GJ',
    parts: [
      {
        name: 'Velocity Air Filter for Ford Mustang 2022',
        partNo: 70145356,
        status: 'waiting',
      },
      {
        name: 'Velocity Air Filter for Ford Mustang 2022',
        partNo: 70145357,
        status: 'arrived',
      },
      {
        name: 'Velocity Air Filter for Ford Mustang 2022',
        partNo: 70145358,
        status: 'completed',
      },
    ],
  },
])

const addToLocalStorage = (item: any) => {
  sessionStorage.setItem('order', JSON.stringify(item))
  OrderDialogRef.value.openDialog()
}
</script>

<template>
  <div>
    <VCard>
      <VCardTitle class="my-3 ms-1 d-flex justify-space-between align-center">
        <h5 class="text-h5 ">
          Repair Orders
        </h5>
        <OrderFormDialog />
      </VCardTitle>
      <VCardText>
        <VRow>
          <VCol
            v-for="item in orders"
            :key="item.orderNo"
          >
            <OrderCard
              style="min-inline-size:  18rem;"
              :item="item"
              @click="addToLocalStorage(item)"
            />
          </VCol>
        </VRow>
      </VCardText>
    </VCard>

    <OrderDialog ref="OrderDialogRef" />
  </div>
</template>
