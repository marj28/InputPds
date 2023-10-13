<template>
  <div>
    <q-card>
      <q-card-section style="max-height: 50vh" class="scroll">
        <div class="text-h6">
         EDUCATIONAL BACKGROUND
          <q-btn
            label="Add"
            @click="secondDialog = true"

          ></q-btn>
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
            <div class="col-md-4 col-sm-4 col-xs-12">
              <q-input
                filled
                v-model="level"
                label="Level"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col-md-8 col-sm-8 col-xs-12">
              <q-input
                filled
                v-model="name"
                label="Name of School"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col-md-12 col-sm-12 col-xs-12">
              <q-input
                filled
                v-model="degree"
                label="Basic Education/Degree/Course"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col-md-6 col-sm-6 col-xs-12">
              <q-input
                filled
                v-model="PeriodofAttendanceFrom"
                label="Period of Attendance From"
                dense
                class="q-pa-sm"
                type="date"
              />
            </div>
            <div class="col-md-6 col-sm-6 col-xs-12">
              <q-input
                filled
                v-model="PeriodofAttendanceTo"
                label="Period of Attendance To"
                dense
                class="q-pa-sm"
                type="date"
              />
            </div>
          </div>
          <div class="row">
            <div class="col-md-6 col-sm-6 col-xs-12">
              <q-input
                filled
                v-model="Unit"
                label="Highest Level / Units Earned"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col-md-6 col-sm-6 col-xs-12">
              <q-input
                filled
                v-model="Unit"
                label="Year Graduated"
                dense
                class="q-pa-sm"
                type="number"
              />
            </div>
            <div class="col-md-12 col-sm-12 col-xs-12">
              <q-input
                filled
                v-model="Unit"
                label="Scholarship / Academic Honors Received"
                dense
                class="q-pa-sm"
                type="number"
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
          name: "Level",
          required: true,
          label: "Level",
          align: "left",
          field: (row) => row.Level,
          format: (val) => `${val}`,
          sortable: true,
        },
        {
          name: "NameofSchool",
          align: "center",
          label: "Name of School",
          field: "NameofSchool",
          sortable: true,
        },
        {
          name: "Degree",
          align: "center",
          label: "Basic Education/Degree/Course",
          field: "Degree",
          sortable: true,
        },
        {
          name: "PeriodofAttendanceFrom",
          align: "center",
          label: "From",
          field: "PeriodofAttendanceFrom",
          sortable: true,
        },
        {
          name: "PeriodofAttendanceTo",
          align: "center",
          label: "To",
          field: "PeriodofAttendanceTo",
          sortable: true,
        },
        {
          name: "Unit",
          align: "center",
          label: "Highest Level/Units Earned",
          field: "Unit",
          sortable: true,
        },
        {
          name: "YearGraduated",
          align: "center",
          label: "Year Graduated",
          field: "YearGraduated",
          sortable: true,
        },
        {
          name: "Scholarship",
          align: "center",
          label: "Scholarship/Academic Honors Received",
          field: "Scholarship",
          sortable: true,
        },
      ],
      rows: [
        {
          Level: "2",
          NameofSchool: "s",
          Degree: "s",
          PeriodofAttendanceFrom: "s",
          PeriodofAttendanceTo: "s",
          Unit: "s",
          YearGraduated: "s",
          Scholarship: "s"
        },
      ],
    };
  },
};
</script>
