<template>
  <div class="d-flex justify-content-center align-items-center text-center min-vh-100 m-0 my-auto">
    <div class="container m-2">
      <div>
        <div
          class="border border-white text-white h4 p-4 mb-4"
          v-html="alert ? alert : 'Select Your State'"
        ></div>

        <div class="form-row p-0">
          <div class="col-12 col-md-6 mb-3">
            <select
              required
              id="state"
              v-model="selectedState"
              @change="(alert = 'Select Your Local Govt. Area')"
              class="form-control form-control-lg border-outline-light rounded-0"
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
              class="form-control form-control-lg border-light rounded-0"
              @change="(alert = `Your Postal Code Is: <strong>${postalCode}</strong>`)"
            >
              <option value disabled selected hidden>Select L.G.A</option>
              <option
                :key="index"
                :value="lga.postalCode"
                v-for="(lga, index) in nigeria[+selectedState].state.lga"
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
      alert: "",
      postalCode: "",
      selectedState: ""
    };
  }
};
</script>


<style>
.alert,
.border,
.form-control {
  border-width: 2px !important;
}

body {
  background-color: #008751;
  background-image: url("/gradient-squares.png");
  /* This is mostly intended for prototyping; please download the pattern and re-host for production environments. Thank you! */
}
</style>
