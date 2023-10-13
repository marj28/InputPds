<template>
  <div>
    <q-card>
      <q-card-section style="max-height: 50vh" class="scroll">
        <div class="text-h6">
          CIVIL SERVICE ELIGIBILITY
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
                v-model="name"
                label="Eligibility"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col">
              <q-input
                filled
                v-model="name"
                label="Rating"
                dense
                class="q-pa-sm"
              />
            </div>
          </div>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="dateofexamination"
                label="Date of Examination"
                dense
                class="q-pa-sm"
                type="date"
              />
            </div>
            <div class="col">
              <q-input
                filled
                v-model="name"
                label="Place of Examination"
                dense
                class="q-pa-sm"
              />
            </div>
          </div>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="name"
                label="License Number"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col">
              <q-input
                filled
                v-model="dateofvalidity"
                label="Date of Validity"
                dense
                class="q-pa-sm"
                type="date"
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
          name: "Eligibility",
          required: true,
          label: "Eligibility",
          align: "left",
          field: (row) => row.Eligibility,
          format: (val) => `${val}`,
          sortable: true,
        },
        {
          name: "Rating",
          align: "center",
          label: "Rating (if Applicable)",
          field: "Rating",
          sortable: true,
        },
        {
          name: "DateofExamination",
          align: "center",
          label: "Date of Examination",
          field: "DateofExamination",
          sortable: true,
        },
        {
          name: "PlaceofExamination",
          align: "center",
          label: "Place of Examination",
          field: "PlaceofExamination",
          sortable: true,
        },
        {
          name: "LicenseNumber",
          align: "center",
          label: "License Number",
          field: "LicenseNumber",
          sortable: true,
        },
        {
          name: "DateofValidity",
          align: "center",
          label: "Date of Validity",
          field: "DateofValidity",
          sortable: true,
        },
      ],
      rows: [
        {
          Eligibility: "2",
          Rating: "s",
          DateofExamination: "s",
          PlaceofExamination: "s",
          LicenseNumber: "s",
          DateofValidity: "s",
        },
      ],
    };
  },
};
</script>
