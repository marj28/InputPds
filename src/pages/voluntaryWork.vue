<template>
  <div>
    <q-card>
      <q-card-section style="max-height: 50vh" class="scroll">
        <div class="text-h6">
          VOLUNTARY WORK
          <q-btn label="Add" @click="secondDialog = true"></q-btn>
        </div>
      </q-card-section>
      <q-table
        class="my-sticky-header-table"
        flat
        bordered
        title=""
        dense
        :rows="rows"
        :columns="columns"
        :filter="filter"
        row-key="id"
      ></q-table>
    </q-card>
    <q-dialog
      v-model="secondDialog"
      persistent
      transition-show="scale"
      transition-hide="scale"
    >
      <q-card class="" style="width: 500px">
        <q-card-section>
          <div class="text-h6">Add Details</div>
        </q-card-section>
        <q-separator />
        <q-card-section>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="Name"
                label="Name and Address of Organization"
                dense
                class="q-pa-sm"
              />
            </div>
          </div>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="InclusiveDateFrom"
                label="Inclusive Date From"
                dense
                class="q-pa-sm"
                type="date"
              />
            </div>
            <div class="col">
              <q-input
                filled
                v-model="InclusiveDateTo"
                label="Inclusive Date To"
                dense
                class="q-pa-sm"
                type="date"
              />
            </div>
          </div>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="NumberofHours"
                label="Number of Hours"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col">
              <q-input
                filled
                v-model="Position"
                label="Position"
                dense
                class="q-pa-sm"
              />
            </div>
          </div>
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Cancel" color="primary" v-close-popup size="md" />
          <q-btn
            label="Save"
            color="secondary"
            size="md"
            v-close-popup
            @click="savehistory(editedItem)"
          />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  data() {
    return {
      secondDialog: false,
      model: ref(null),
      name: "",
      dateofbirth: "",
      columns: [
        {
          name: "Name",
          required: true,
          label: "NAME & ADDRESS OF ORGANIZATION",
          align: "left",
          field: (row) => row.Name,
          format: (val) => `${val}`,
          sortable: true,
        },
        {
          name: "InclusiveDateFrom",
          align: "center",
          label: "From",
          field: "InclusiveDateFrom",
          sortable: true,
        },
        {
          name: "InclusiveDateTo",
          align: "center",
          label: "To",
          field: "InclusiveDateTo",
          sortable: true,
        },
        {
          name: "NumberofHours",
          align: "center",
          label: "Number of Hours",
          field: "NumberofHours",
          sortable: true,
        },
        {
          name: "Position",
          align: "center",
          label: "Position",
          field: "Position",
          sortable: true,
        },
      ],
      rows: [
        {
          Name: "2",
          InclusiveDateFrom: "s",
          InclusiveDateTo: "s",
          NumberofHours: "s",
          Position: "s",
        },
        {
          Name: "2",
          InclusiveDateFrom: "s",
          InclusiveDateTo: "s",
          NumberofHours: "s",
          Position: "s",
        },
        {
          Name: "2",
          InclusiveDateFrom: "s",
          InclusiveDateTo: "s",
          NumberofHours: "s",
          Position: "s",
        },
        {
          Name: "2",
          InclusiveDateFrom: "s",
          InclusiveDateTo: "s",
          NumberofHours: "s",
          Position: "s",
        },
        {
          Name: "2",
          InclusiveDateFrom: "s",
          InclusiveDateTo: "s",
          NumberofHours: "s",
          Position: "s",
        },








      ],
    };
  },
};
</script>
