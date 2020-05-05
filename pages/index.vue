<template>
  <div class="d-flex justify-content-center align-items-center text-center min-vh-100 m-0 my-auto">
    <div class="container m-2">
      <div>
        <div
          class="border border-white text-white rounded h4 p-4 mb-4"
          v-html="alert ? alert : 'Select Your State'"
        ></div>

        <div class="form-row p -5">
          <div class="col-12 col-md-5 mb-3">
            <select
              required
              v-model="selectedState"
              @change="(alert = 'Select Your Local Govt. Area')"
              class="form-control form-control-lg border-outline-light"
            >
              <option value disabled selected hidden>Select State</option>
              <template v-for="(states, index) in nigeria">
                <option :key="index" :value="index">{{states.state.name}}</option>
              </template>
            </select>
          </div>

          <div class="col-12 col-md-4 mb-4">
            <select
              required
              v-model="postalCode"
              class="form-control form-control-lg border-light"
              @change="(alert = `Your Postal Code Is: <strong>${postalCode}</strong>`)"
            >
              <option value disabled selected hidden>Select Local Govt. Area</option>
              <option
                :key="index"
                :value="lga.postalCode"
                v-for="(lga, index) in nigeria[+selectedState].state.lga"
              >{{lga.name}}</option>
            </select>
          </div>

          <div class="col-12 col-md-3 mb-3">
            <select disabled required class="form-control form-control-lg border-light">
              <option value disabled selected hidden>Select District</option>
            </select>
          </div>
        </div>
      </div>

      <div class="pt-4 font-weight-bold">
        <a href="//github.com/OgbeniHMMD/nigeria-postalcode">Version 0.0.2 (dev)</a>
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
body {
  background-color: #008751;
  background-image: url("/gradient-squares.png");
  /* This is mostly intended for prototyping; please download the pattern and re-host for production environments. Thank you! */
}
a {
  color: white;
}

.alert,
.border,
.form-control {
  border-width: 2px !important;
}
</style>
