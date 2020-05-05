<template>
  <div class="d-flex justify-content-center align-items-center text-center min-vh-100 m-0 my-auto">
    <div class="container m-2">
      <div class="border border-dark p-2 p-md-5">
        <div v-if="!postalCode" class="h2 mb-5">Nigeria's Postal Code Finder</div>
        <div v-else class="h2 mb-5">Postal Code: {{postalCode}}</div>

        <div class="form-row p-0">
          <div class="col-12 col-md-6 mb-3">
            <select
              required
              id="state"
              v-model="selectedState"
              @change="clearVariables"
              class="form-control form-control-lg border-dark"
            >
              <option value disabled selected hidden>Select State</option>
              <template v-for="(states, index) in nigeria">
                <option :key="index" :value="index">{{states.state.name}}</option>
              </template>
            </select>
          </div>

          <div class="col-12 col-md-6 mb-3">
            <select
              id="lga"
              required
              v-model="postalCode"
              class="form-control form-control-lg border-dark"
            >
              <option value disabled selected hidden>Select L.G.A</option>
              <option
                v-for="(lga, index) in nigeria[+selectedState].state.lga"
                :key="index"
                :value="++index"
              >{{lga.name}}</option>
            </select>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import nigeria from "~/assets/JSON/nigeria.json";

export default {
  data: function() {
    return {
      nigeria,
      selectedState: "",
      postalCode: ""
    };
  },
  methods: {
    clearVariables() {
      this.postalCode = "";
      //this.postalCode = nigeria[this.selectedState]
    }
  }
};
</script>


<style>
.border,
.form-control {
  border-width: 2px !important;
}
</style>
