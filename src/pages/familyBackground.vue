<template>
  <div>
    <q-card>
      <q-form>
        <div class="row">
          <div class="col-md-6 col-xs-12">
            <q-input filled label="Spouse's Surname" dense class="q-pa-sm" />
          </div>
          <div class="col-md-6 col-xs-12">
            <q-input filled label="Spouse's Firstname" class="q-pa-sm" dense />
          </div>
          <div class="col-md-6 col-xs-6">
            <q-input filled label="Spouse's Middlename" dense class="q-pa-sm" />
          </div>
          <div class="col-md-6 col-xs-6 q-pa-sm">
            <!-- <q-input filled label="Name Extension" dense class="q-pa-sm" /> -->
            <q-select
              filled
              v-model="model"
              use-input
              dense
              input-debounce="0"
              label="Name Extension"
              :options="extension"
              @filter="filterFn"
              style="min-width: 70%; max-width: 98%"
              behavior="menu"
            >
              <template v-slot:no-option>
                <q-item>
                  <q-item-section class="text-grey">
                    No results
                  </q-item-section>
                </q-item>
              </template>
            </q-select>
          </div>
        </div>
        <div class="row">
          <div class="col-md-3 col-xs-12">
            <q-input filled label="Occupation" dense class="q-pa-sm" />
          </div>
          <div class="col-md-3 col-xs-12">
            <q-input
              filled
              label="Employers / Business Name"
              class="q-pa-sm"
              dense
            />
          </div>
          <div class="col-md-3 col-xs-12">
            <q-input filled label="Business Address" class="q-pa-sm" dense />
          </div>
          <div class="col-md-3 col-xs-12">
            <q-input
              filled
              label="Telephone Number"
              class="q-pa-sm"
              dense
              type="number"
            />
          </div>
        </div>
        <div class="row">
          <div class="col-md-6 col-xs-12">
            <q-input filled label="Father's Surname" dense class="q-pa-sm" />
          </div>
          <div class="col-md-6 col-xs-12">
            <q-input filled label="Father's Firstname" class="q-pa-sm" dense />
          </div>
          <div class="col-md-6 col-xs-6">
            <q-input filled label="Father's Middlename" dense class="q-pa-sm" />
          </div>
          <div class="col-md-6 col-xs-6 q-pa-sm">
            <!-- <q-input filled label="Name Extension" dense class="q-pa-sm" /> -->
            <q-select
              filled
              v-model="model"
              use-input
              dense
              input-debounce="0"
              label="Name Extension"
              :options="extension"
              @filter="filterFn"
              style="min-width: 70%; max-width: 98%"
              behavior="menu"
            >
              <template v-slot:no-option>
                <q-item>
                  <q-item-section class="text-grey">
                    No results
                  </q-item-section>
                </q-item>
              </template>
            </q-select>
          </div>
        </div>
        <div class="row">
          <div class="col-md-4 col-xs-12">
            <q-input
              filled
              label="Mother's Maiden Surname"
              dense
              class="q-pa-sm"
            />
          </div>
          <div class="col-md-4 col-xs-12">
            <q-input filled label="Mother's Firstname" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-12">
            <q-input
              filled
              label="Mother's Maiden Middlename"
              dense
              class="q-pa-sm"
            />
          </div>
        </div>

        <div class="q-pa-sm">
          <q-card >
            <q-card-section style="max-height: 50vh" class="scroll">
              <div class="text-h6">
                CHILDREN NAMES
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
                <div class="text-h6">Add Children</div>
              </q-card-section>
              <q-separator />
              <q-card-section>
                <div class="row">
                  <div class="col">
                    <q-input
                      filled
                      v-model="name"
                      label="Name of Children"
                      dense
                      class="q-pa-sm"
                    />
                  </div>
                </div>
                <div class="row">
                  <div class="col">
                    <q-input
                      filled
                      v-model="dateofbirth"
                      label="Date of Birth"
                      dense
                      class="q-pa-sm"
                      type="date"
                    />
                  </div>
                </div>
              </q-card-section>

              <q-card-actions align="right">
                <q-btn
                  flat
                  label="Cancel"
                  color="primary"
                  v-close-popup
                  size="md"
                />
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
      </q-form>
    </q-card>
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
      cit: ref(null),
      extension: ["Jr.", "Sr.", "III"],
      columns: [
        {
          name: "lastname",
          required: true,
          label: "Name of Children",
          align: "left",
          field: (row) => row.lastName,
          format: (val) => `${val}`,
          sortable: true,
        },
        {
          name: "firstname",
          align: "center",
          label: "Date of Birth",
          field: "firstName",
          sortable: true,
        },
      ],
      rows: [
        {
          lastName: "Honey Curay",
          firstName: "11-28-99",
        },
      ],
    };
  },
};
</script>
