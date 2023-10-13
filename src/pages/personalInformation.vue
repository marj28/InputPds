<template>
  <div>
    <q-card>
      <q-form>
        <div class="row">
          <div class="col-md-6 col-xs-12">
            <q-input filled label="Lastname" dense class="q-pa-sm" />
          </div>
          <div class="col-md-6 col-xs-12">
            <q-input filled label="Firstname" class="q-pa-sm" dense />
          </div>
        </div>
        <div class="row">
          <div class="col-md-6 col-xs-6">
            <q-input filled label="Middlename" dense class="q-pa-sm" />
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
          <div class="col-md-6 col-xs-6">
            <q-input
              filled
              label="Date of Birth"
              dense
              class="q-pa-sm"
              type="date"
            />
          </div>
          <div class="col-md-6 col-xs-6">
            <q-input filled label="Place of Birth" class="q-pa-sm" dense />
          </div>
        </div>

        <div class="row">
          <div class="col-md-6 col-xs-6 q-pa-sm">
            <q-select
              filled
              v-model="Sex"
              use-input
              dense
              input-debounce="0"
              label="Sex"
              :options="sex"
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

          <div class="col-md-6 col-xs-6 q-pa-sm">
            <q-select
              filled
              v-model="model"
              use-input
              dense
              input-debounce="0"
              label="Civil Status"
              :options="status"
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
          <div class="col-md-6 col-xs-6 q-pa-sm">
            <q-select
              filled
              v-model="Gender"
              use-input
              dense
              input-debounce="0"
              label="Gender Preference"
              :options="genderPreference"
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
          <div class="col-md-6 col-xs-6">
            <q-input filled label="Height (m)" dense class="q-pa-sm" />
          </div>
          <div class="col-md-6 col-xs-6">
            <q-input filled label="Weight (kg)" class="q-pa-sm" dense />
          </div>
          <div class="col-md-6 col-xs-6">
            <q-input filled label="Blood Type" class="q-pa-sm" dense />
          </div>
        </div>
        <q-separator inset></q-separator>
        <div class="row">
          <div class="col-md-4 col-xs-6">
            <q-input filled label="GSIS ID NO." dense class="q-pa-sm" />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="PAGIBIG ID NO." class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="PHILHEALTH ID NO." class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="SSS NO." dense class="q-pa-sm" />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="TIN NO." class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input
              filled
              label="AGENCY EMPLOYEE NO."
              class="q-pa-sm"
              dense
              type=""
            />
          </div>
        </div>
        <q-separator inset></q-separator>
        <div class="row">
          <div class="col-md-6 col-xs-12 q-pa-sm">
            <q-select
              filled
              v-model="cit"
              use-input
              dense
              input-debounce="0"
              label="Citizenship"
              :options="citizenship"
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
          <div class="col-md-6 col-xs-6 q-pa-sm" v-if="cit === 'Filipino'">
            <q-radio v-model="citizenshipStatus" val="byBirth" label="by birth" inline />
            <q-radio
              v-model="citizenshipStatus"
              val="byNaturalization"
              label="by naturalization"
              inline
            />
          </div>
          <div class="col-md-6 col-xs-6 " v-if="cit === 'Dual Citizenship'">
            <q-input
              filled
              label="Please Indicate Country"
              class="q-pa-sm"
              dense
              type=""
            />
          </div>
        </div>
        <q-separator inset></q-separator>
        <label for="Address" class="q-mb-md q-ml-lg q-mt-md"
          >Types of Disabilities:
        </label>
        <div class="q-pa-md">
          <div class="q-gutter-sm">
            <q-checkbox
              v-model="Psychosocial"
              label="Psychosocial Disability"
            />
            <q-checkbox
              v-model="Chronic"
              label="Disability Caused by Chronic Illness"
            />
            <q-checkbox
              v-model="Learning"
              label="Learning Disability"
            />
            <q-checkbox
              v-model="Mental"
              label="Mental Disability"
            />
            <q-checkbox keep-color v-model="Visual" label="Visual Disability" />
            <q-checkbox
              keep-color
              v-model="Orthopedic"
              label="Orthopedic Disability"
            />
            <q-checkbox
              keep-color
              v-model="Communication"
              label="Communication Disability"
            />
          </div>
        </div>
        <q-separator inset />
        <div class="row">
          <div class="col-md-6 col-xs-6 q-pa-sm">
            <label for="Address"
              >Indigenous Groups:
            </label>
            <div class="">
              <q-select
                filled
                v-model="selectedIndigenous"
                use-input
                dense
                input-debounce="0"
                label="Indigenous People"
                :options="indigenousGroup"
                @filter="filterIndigenous"
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
          <div class="col-md-6 col-xs-6 q-pa-sm">
            <label for="Address"
              >Religious Sector:
            </label>
            <div class="">
              <q-select
                filled
                v-model="selectedReligion"
                use-input
                dense
                input-debounce="0"
                label="Religious Sector"
                :options="religion"
                @filter="filterFn"
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
        </div>

        <q-separator inset />
        <label for="Address" class="q-mb-md q-ml-sm q-mt-md"
          >Residential Address:
        </label>
        <div class="row">
          <div class="col-md-4 col-xs-6">
            <q-input filled label="Region" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="Province" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="City/Municipality" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="Baranggay" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-12">
            <q-input filled label="Subdivision/Village" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-12">
            <q-input filled label="Street" class="q-pa-sm" dense />
          </div>
          <div class="col-md-8 col-xs-6">
            <q-input filled label="House/Block/Lot No." dense class="q-pa-sm" />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="ZIP CODE" class="q-pa-sm" dense />
          </div>
        </div>

        <label for="Address" class="q-mb-md q-ml-sm q-mt-md"
          >Permanent Address:
        </label>
       <q-checkbox
              v-model="permanentAddress"
              label="Same as Residential Address"
              size="xs"
            />
        <div class="row">
          <div class="col-md-4 col-xs-6">
            <q-input filled label="Region" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="Province" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="City/Municipality" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="Baranggay" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-12">
            <q-input filled label="Subdivision/Village" class="q-pa-sm" dense />
          </div>
          <div class="col-md-4 col-xs-12">
            <q-input filled label="Street" class="q-pa-sm" dense />
          </div>
          <div class="col-md-8 col-xs-6">
            <q-input filled label="House/Block/Lot No." dense class="q-pa-sm" />
          </div>
          <div class="col-md-4 col-xs-6">
            <q-input filled label="ZIP CODE" class="q-pa-sm" dense />
          </div>
        </div>
      </q-form>
    </q-card>
  </div>
</template>

<script>
import { ref } from "vue";

const stringReligion = [
  "Roman Catholic",
  "Islam",
  "Iglesia ni Cristo",
  "Philippine Independent Church",
  "Jesus Miracle Crusade International Ministry",
  "Seventh-Day Adventist",
  "Bible Baptist Church",
  "United Church of Christ in the Philippines",
  "Jehova's Witnesses",
  "Church of Christ",
  "Protestantism",
  "Members of God Church International",
  "Most Holy Church of God in Christ Jesus",
  "Apostolic Catholic Church",
  "Orthodoxy",
  "The Church of Jesus Christ of Latter-Day Saints",
  "Other Religious Affiliations",
];
const stringIndigenous = [
  "Igorot",
  "Mangyan",
  "Ibaloi",
  "Tagbanwa",
  "Mandaya",
  "Ifugao People",
  "Batak People",
  "Moro People",
  "Tausug People",
  "Kalinga",
  "Visayans",
  "Sama-Bajau",
  "Mamanwa",
  "Palawan People",
  "Tboli People",
  "Ilocano People",
  "Lumad",
  "Negrito",
  "Blaan People",
  "Bukidnon",
  "Aeta People",
  "Tagabawa",
  "Bicolano People",
  "Bontoc People",
  "Mansaka",
];

export default {
  data() {
    return {
      stringReligion: [],
      stringIndigenous: [],
      permanentAddress : false,
      cit: "",
      Gender: "",
      byBirth: false,
      citizenshipStatus: '',
      byNaturalization: false,
      Psychosocial: false,
      Chronic: false,
      Learning: false,
      Mental: false,
      Visual: false,
      Orthopedic: false,
      Communication: false,
      status: ["Single", "Married", "Widowed", "Separated", "Other/s"],
      citizenship: ["Filipino", "Dual Citizenship"],
      sex: ["Male", "Female"],
      genderPreference: [
        "Lesbian",
        "Gay",
        "Bisexual",
        "Transgender",
        "Queer",
        "Intersex",
        "Asexual",
        "+",
      ],
      extension: ["Jr.", "Sr.", "III"],
    };
  },
  setup() {
    const religion = ref(stringReligion);
    const indigenousGroup = ref(stringIndigenous);

    return {
      selectedReligion: ref(null),
      religion,
      selectedIndigenous: ref(null),
      indigenousGroup,

      filterFn(val, update) {
        if (val === "") {
          update(() => {
            religion.value = stringReligion;

            // here you have access to "ref" which
            // is the Vue reference of the QSelect
          });
          return;
        }

        update(() => {
          const needle = val.toLowerCase();
          religion.value = stringReligion.filter(
            (v) => v.toLowerCase().indexOf(needle) > -1
          );
        });
      },

      filterIndigenous(val, update) {
        if (val === "") {
          update(() => {
            indigenousGroup.value = stringIndigenous;
          });
          return;
        }
        update(() => {
          const needle = val.toLowerCase();
          indigenousGroup.value = stringIndigenous.filter(
            (v) => v.toLowerCase().indexOf(needle) > -1
          );
        });
      },
    };
  },
};
</script>
