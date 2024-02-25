import partsVue from '@/pages/parts.vue';
import partsVue from '@/pages/parts.vue';
import { log } from 'console';
<script setup lang="ts">
const isDialogOpen = ref(false)
const isPartDialogOpen = ref(false)
const selectedStatus = ref('')

const partTemp = ref({
  name: null,
  partNo: null,
  status: null,
})

const addPart = (status: string) => {
  selectedStatus.value = status
  isPartDialogOpen.value = true
}

const form = ref({
  repairNo: null,
  serviceType: null,
  parts: [{
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
  }],
})

const addParts = (status: string) => {
  partTemp.value.status = status

  form.value.parts.push({ ...partTemp.value })
  form.value.name = ''
  form.value.partNo = ''
  form.value.status = ''

  isPartDialogOpen.value = false
}
</script>

<template>
  <div>
    <VBtn @click="isDialogOpen = !isDialogOpen">
      <VIcon icon="ri-add-fill" />
      Add Repair Job
    </VBtn>

    <VDialog v-model="isDialogOpen">
      <VCard
        title="Add Repair Job"
        max-width="800"
        min-width="300"
        class="mx-auto"
      >
        <VCardText>
          <VForm>
            <VRow>
              <VCol cols="12">
                <VTextField
                  v-model="form.repairNo"
                  label="Repair No."
                />
              </VCol>
              <VCol cols="12">
                <h6 class="text-body-2 me-3">
                  Type of Service:
                </h6>
                <VRadioGroup
                  v-model="form.serviceType"
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
              </VCol>
              <VCol>
                <VRow>
                  <VCol>
                    <div class="d-flex align-center justify-space-between">
                      <div>
                        Completed Parts
                      </div>
                      <VBtn
                        icon="ri-add-line"
                        variant="text"
                        @click="addPart('completed')"
                      />
                    </div>
                    <div class="d-flex flex-column gap-y-1">
                      <VCard
                        v-for="part in form.parts.filter(part => part.status === 'completed')"
                        :key="part.partNo"
                      >
                        <VCardText class="d-flex justify-space-between">
                          <div>
                            <b>{{ part.name }}</b>
                            <h6 class="text-body-2">
                              Part No: {{ part.partNo }}
                            </h6>
                          </div>
                          <div class="d-flex align-center">
                            <VBtn
                              variant="text"
                              density="compact"
                              icon="ri-delete-bin-line"
                            />
                          </div>
                        </VCardText>
                      </VCard>
                    </div>
                  </VCol>
                  <VDivider vertical />
                  <VCol>
                    <div class="d-flex align-center justify-space-between">
                      <div>
                        Arrived Parts
                      </div>
                      <VBtn
                        icon="ri-add-line"
                        variant="text"
                        @click="addPart('arrived')"
                      />
                    </div>
                    <div class="d-flex flex-column gap-y-1">
                      <VCard
                        v-for="part in form.parts.filter(part => part.status === 'arrived')"
                        :key="part.partNo"
                      >
                        <VCardText class="d-flex justify-space-between">
                          <div>
                            <b>{{ part.name }}</b>
                            <h6 class="text-body-2">
                              Part No: {{ part.partNo }}
                            </h6>
                          </div>
                          <div class="d-flex align-center">
                            <VBtn
                              variant="text"
                              density="compact"
                              icon="ri-delete-bin-line"
                            />
                          </div>
                        </VCardText>
                      </VCard>
                    </div>
                  </VCol>
                  <VDivider vertical />
                  <VCol>
                    <div class="d-flex align-center justify-space-between">
                      <div>
                        Waiting Parts
                      </div>
                      <VBtn
                        icon="ri-add-line"
                        variant="text"
                        @click="addPart('waiting')"
                      />
                    </div>
                    <div class="d-flex flex-column gap-y-1">
                      <VCard
                        v-for="part in form.parts.filter(part => part.status === 'waiting')"
                        :key="part.partNo"
                      >
                        <VCardText class="d-flex justify-space-between">
                          <div>
                            <b>{{ part.name }}</b>
                            <h6 class="text-body-2">
                              Part No: {{ part.partNo }}
                            </h6>
                          </div>
                          <div class="d-flex align-center">
                            <VBtn
                              variant="text"
                              density="compact"
                              icon="ri-delete-bin-line"
                            />
                          </div>
                        </VCardText>
                      </VCard>
                    </div>
                  </VCol>
                </VRow>
              </VCol>
            </VRow>
          </VForm>
        </VCardText>
        <VCardActions class="pb-3 px-4 d-flex justify-end">
          <VBtn @click="isDialogOpen = false">
            Cancel
          </VBtn>
          <VBtn variant="outlined">
            Apply
          </VBtn>
        </VCardActions>
      </VCard>

      <!-- Dialog to add parts -->
    </VDialog>
    <VDialog v-model="isPartDialogOpen">
      <VCard
        title="Add Part"
        max-width="500"
        min-width="300"
        class="mx-auto"
      >
        <VCardText>
          <VRow>
            <VCol cols="12">
              <VTextField
                v-model="partTemp.name"
                label="Part Name"
              />
            </VCol>
            <VCol cols="12">
              <VTextField
                v-model="partTemp.partNo"
                label="Part Number"
              />
            </VCol>
          </VRow>
        </VCardText>
        <VCardActions class="d-flex justify-end pe-5 pb-5">
          <VBtn
            variant="text"
            @click="isPartDialogOpen = false"
          >
            Cancel
          </VBtn>
          <VBtn
            variant="outlined"
            @click="addParts(selectedStatus)"
          >
            Add
          </VBtn>
        </VCardActions>
      </VCard>
    </VDialog>
  </div>
</template>
