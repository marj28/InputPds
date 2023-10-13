<template>
  <div>
    <div class="row">
      <div class="col-md-4 col-sm-12 col-xs-12 q-pa-xs">
        <q-card>
          <q-card-section  class="scroll">
            <div class="text-h6">
              SPECIAL SKILLS AND HOBBIES
              <q-btn label="Add" @click="SkillDialog = true"></q-btn>
            </div>
          </q-card-section>
          <q-table
            class="my-sticky-header-table"
            flat
            bordered
            title=""
            dense
            :rows="rowSkills"
            :columns="columnSkills"
            :filter="filter"
            row-key="id"
          ></q-table>
        </q-card>
      </div>
      <div class="col-md-4 col-sm-12 col-xs-12 q-pa-xs">
        <!-- NON-ACADEMIC DISTINCTIONS / RECOGNITION -->
        <q-card>
          <q-card-section  class="scroll">
            <div class="text-h6">
              NON-ACADEMIC DISTINCTIONS
              <q-btn label="Add" @click="NonAcademicDialog = true"></q-btn>
            </div>
          </q-card-section>
          <q-table
            class="my-sticky-header-table"
            flat
            bordered
            title=""
            dense
            :rows="rowAcademic"
            :columns="columnAcademic"
            :filter="filter"
            row-key="id"
          ></q-table>
        </q-card>
      </div>
      <div class="col-md-4 col-sm-12 col-xs-12 q-pa-xs">
        <!-- MEMBERSHIP IN ASSOCIATION/ORGANIZATION -->
        <q-card>
          <q-card-section  class="scroll">
            <div class="text-h6">
              MEMBERSHIP IN ASSOCIATION
              <q-btn label="Add" @click="MembershipDialog = true"></q-btn>
            </div>
          </q-card-section>
          <q-table
            class="my-sticky-header-table"
            flat
            bordered
            title=""
            dense
            :rows="rowMembership"
            :columns="columnMembership"
            :filter="filter"
            row-key="id"
          ></q-table>
        </q-card>
      </div>
    </div>

    <q-dialog
      v-model="SkillDialog"
      persistent
      transition-show="scale"
      transition-hide="scale"
    >
      <q-card class="" style="width: 500px">
        <q-card-section>
          <div class="text-h6">Add</div>
        </q-card-section>
        <q-separator />
        <q-card-section>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="SkillsandHobbies"
                label="Skills and Hobbies"
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
    <!-- NON-ACADEMIC -->
    <q-dialog
      v-model="NonAcademicDialog"
      persistent
      transition-show="scale"
      transition-hide="scale"
    >
      <q-card class="" style="width: 500px">
        <q-card-section>
          <div class="text-h6">Add</div>
        </q-card-section>
        <q-separator />
        <q-card-section>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="NonAcademic"
                label="NON-ACADEMIC DISTINCTIONS / RECOGNITION    "
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

    <!-- MEMBERSHIP IN ASSOCIATION/ORGANIZATION   -->
    <q-dialog
      v-model="MembershipDialog"
      persistent
      transition-show="scale"
      transition-hide="scale"
    >
      <q-card class="" style="width: 500px">
        <q-card-section>
          <div class="text-h6">Add</div>
        </q-card-section>
        <q-separator />
        <q-card-section>
          <div class="row">
            <div class="col">
              <q-input
                filled
                v-model="Membership"
                label="MEMBERSHIP IN ASSOCIATION/ORGANIZATION      "
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
      SkillDialog: false,
      NonAcademicDialog: false,
      MembershipDialog: false,
      model: ref(null),
      name: "",
      dateofbirth: "",
      columnSkills: [
        {
          name: "SkillsandHobbies",
          required: true,
          label: "Skills and Hobbies",
          align: "left",
          field: (row) => row.SkillsandHobbies,
          format: (val) => `${val}`,
          sortable: true,
        },
      ],
      rowSkills: [
        {
          SkillsandHobbies: "Listening",
        },
        {
          SkillsandHobbies: "Listening",
        },
        {
          SkillsandHobbies: "Listening",
        },
        {
          SkillsandHobbies: "Listening",
        },
        {
          SkillsandHobbies: "Listening",
        },

      ],
      columnAcademic: [
        {
          name: "NonAcademic",
          required: true,
          label: "Non-Academic Distinction",
          align: "left",
          field: (row) => row.NonAcademic,
          format: (val) => `${val}`,
          sortable: true,
        },
      ],
      rowAcademic: [
        {
          NonAcademic: "Listening",
        },
        {
          NonAcademic: "Listening",
        },
        {
          NonAcademic: "Listening",
        },

        {
          NonAcademic: "Listening",
        },
        {
          NonAcademic: "Listening",
        },
      ],
      columnMembership: [
        {
          name: "Membership",
          required: true,
          label: "Membership in Organization",
          align: "left",
          field: (row) => row.Membership,
          format: (val) => `${val}`,
          sortable: true,
        },

      ],
      rowMembership: [
        {
          Membership: "Listening",
        },
        {
          Membership: "Listening",
        },
        {
          Membership: "Listening",
        },
        {
          Membership: "Listening",
        },
        {
          Membership: "Listening",
        },
      ],
    };
  },
};
</script>
