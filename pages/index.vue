<template>
  <div class="d-flex justify-content-center align-items-center text-center min-vh-100 m-0 my-auto">
    <div class="container m-2">
      <div>
        <div
          class="alert p-4 mb-4"
          :class="alert.type ? alert.type : 'alert-danger'"
          v-html="alert.message ? alert.message : 'Select Your State'"
        ></div>

        <div class="form-row p-0">
          <div class="col-12 col-md-6 mb-3">
            <select
              required
              id="state"
              v-model="selectedState"
              @change="showAlert('alert-warning', 'Select Your L.G.A')"
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
              @change="showAlert('alert-success', `Your Postal Code Is: <strong>${postalCode}</strong>`)"
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
      postalCode: "",

      showPostal: "",
      alert: []
    };
  },
  methods: {
    showAlert(type, msg) {
      this.alert.type = type;
      this.alert.message = msg;
    }
  }
};
</script>


<style>
.alert,
.border,
.form-control {
  //border-width: 2px !important;
}

body {
  background-color: #078700;
  background-image: url("https://www.transparenttextures.com/patterns/clean-gray-paper.png");
  /* This is mostly intended for prototyping; please download the pattern and re-host for production environments. Thank you! */
}
</style>
