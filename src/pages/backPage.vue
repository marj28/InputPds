<template>
  <div>
    <q-card>
      <q-card-section>
        34. Are you related by consanguinity or affinity to the appointing or
        recommending authority, or to the chief of bureau or office or to the
        person who has immediate supervision over you in the Office, Bureau or
        Department where you will be apppointed,
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <label for="sex" class="q-ml-lg">a. within the third degree?</label>
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <label for="sex" class="q-ml-lg"
            >b. within the fourth degree (for Local Government Unit - Career
            Employees)?</label
          >
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
      </q-card-section>
      <q-card-section>
        35. a. Have you ever been found guilty of any administrative offense?

        <q-radio v-model="shape" val="Yes" label="Yes" inline />
        <q-radio v-model="shape" val="No" label="No" inline />

        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <label for="sex" class="q-ml-lg"
            >b. Have you been criminally charged before any court?</label
          >
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
      </q-card-section>
      <q-card-section>
        36. Have you ever been convicted of any crime or violation of any law,
        decree, ordinance or regulation by any court or tribunal?
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
      </q-card-section>
      <q-card-section>
        37. Have you ever been separated from the service in any of the
        following modes: resignation, retirement, dropped from the rolls,
        dismissal, termination, end of term, finished contract or phased out
        (abolition) in the public or private sector?
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
      </q-card-section>
      <q-card-section>
        38. a. Have you ever been a candidate in a national or local election
        held within the last year (except Barangay election)?
        <q-radio v-model="shape" val="Yes" label="Yes" inline />
        <q-radio v-model="shape" val="No" label="No" inline />
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <label for="sex" class="q-ml-lg"
            >b. Have you resigned from the government service during the three
            (3)-month period before the last election to promote/actively
            campaign for a national or local candidate?</label
          >
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
      </q-card-section>
      <q-card-section>
        39. Have you acquired the status of an immigrant or permanent resident
        of another country?
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
      </q-card-section>
      <q-card-section>
        40. Pursuant to: (a) Indigenous People's Act (RA 8371); (b) Magna Carta
        for Disabled Persons (RA 7277); and (c) Solo Parents Welfare Act of 2000
        (RA 8972), please answer the following items:
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <label for="sex" class="q-ml-lg"
            >a. Are you a member of any indigenous group?</label
          >
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <label for="sex" class="q-ml-lg"
            >b. Are you a person with disability?</label
          >
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
        <div class="q-gutter-sm q-mr-md col-md-6 col-xs-12">
          <label for="sex" class="q-ml-lg">c. Are you a solo parent?</label>
          <q-radio v-model="shape" val="Yes" label="Yes" inline />
          <q-radio v-model="shape" val="No" label="No" inline />
        </div>
        <q-separator></q-separator>
        <q-card-section style="max-height: 50vh" class="scroll">
          <div class="text-h6">
            REFERENCES
            <q-btn label="Add" @click="ReferenceDialog = true"></q-btn>
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
      </q-card-section>
      <q-card-section>
        <label for="ID">ID</label>
        <q-input
          @update:model-value="
            (val) => {
              file = val[0];
            }
          "
          filled
          type="file"
          hint="Native file"
        />
      </q-card-section>
    </q-card>
    <q-dialog
      v-model="ReferenceDialog"
      persistent
      transition-show="scale"
      transition-hide="scale"
    >
      <q-card class="" style="width: 500px">
        <q-card-section>
          <div class="text-h6">Add Reference Details</div>
        </q-card-section>
        <q-separator />
        <q-card-section>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="Name"
                label="Reference Name"
                dense
                class="q-pa-sm"
              />
            </div>
          </div>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="Address"
                label="Address"
                dense
                class="q-pa-sm"
              />
            </div>
            <div class="col">
              <q-input
                filled
                v-model="ContactNo"
                label="Contact No. / Telephone No."
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
export default {
  data() {
    return {
      ReferenceDialog: false,
      columns: [
        {
          name: "Name",
          align: "left",
          label: "Name",
          field: "Name",
          sortable: true,
        },
        {
          name: "Address",
          align: "center",
          label: "Address",
          field: "Address",
          sortable: true,
        },
        {
          name: "ContactNo",
          align: "center",
          label: "Contact Number",
          field: "ContactNo",
          sortable: true,
        },
      ],
      rows: [
        {
          Name: "Test",
          Address: "Test",
          ContactNo: "45612",
        },
      ],
    };
  },
};
</script>
