<template>
  <div>
    <q-card>
      <q-card-section style="max-height: 50vh" class="scroll">
        <div class="text-h6">
          WORK EXPERIENCE
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
          <div class="text-h6">Add Work Details</div>
        </q-card-section>
        <q-separator />
        <q-card-section>
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
                v-model="PositionTitle"
                label="Position Title"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col">
              <q-input
                filled
                v-model="Department"
                label="Department"
                dense
                class="q-pa-sm"
              />
            </div>
          </div>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="MonthlySalary"
                label="Monthly Salary"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col">
              <q-input
                filled
                v-model="SalaryGrade"
                label="Salary Grade"
                dense
                class="q-pa-sm"
              />
            </div>
          </div>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="StatusofAppointment"
                label="Status of Appointment"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col">
              <div class="q-gutter-sm q-mt-sm q-ml-sm">
                <label for="">Government Service</label>
                <br>
                <q-radio
                  v-model="shape"
                  checked-icon="task_alt"
                  unchecked-icon="panorama_fish_eye"
                  val="yes"
                  dense
                  label="Yes"
                />
                <q-radio
                  v-model="shape"
                  checked-icon="task_alt"
                  unchecked-icon="panorama_fish_eye"
                  val="no"
                  dense
                  label="No"
                />
              </div>
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
          name: "InclusiveDateFrom",
          required: true,
          label: "From",
          align: "left",
          field: (row) => row.InclusiveDateFrom,
          format: (val) => `${val}`,
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
          name: "PositionTitle",
          align: "center",
          label: "PositionTitle",
          field: "PositionTitle",
          sortable: true,
        },
        {
          name: "Department",
          align: "center",
          label: "Department",
          field: "Department",
          sortable: true,
        },
        {
          name: "MonthlySalary",
          align: "center",
          label: "Monthly Salary",
          field: "MonthlySalary",
          sortable: true,
        },
        {
          name: "SalaryGrade",
          align: "center",
          label: "Salary Grade",
          field: "SalaryGrade",
          sortable: true,
        },
        {
          name: "StatusofAppointment",
          align: "center",
          label: "Status of Appointment",
          field: "StatusofAppointment",
          sortable: true,
        },
        {
          name: "GovtService",
          align: "center",
          label: "Gov't Service",
          field: "GovtService",
          sortable: true,
        },
      ],
      rows: [
        {
          InclusiveDateFrom: "2",
          InclusiveDateTo: "s",
          PositionTitle: "s",
          Department: "s",
          MonthlySalary: "s",
          SalaryGrade: "s",
          StatusofAppointment: "s",
          GovtService: "s",
        },
      ],
    };
  },
};
</script>
