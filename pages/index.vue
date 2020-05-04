<template>
  <div
    class="d-flex justify-content-center align-item-center min-vh-100 border-primary border-bottom text-center m-0 my-auto"
  >
    <div class="container border border-dark m-2">
      <div class="p-2 p-md-5">
        <div class="title h2 mb-5">Nigeria's Postal Code Finder</div>
        {{ nigeria.state }}
        <div class="form-row p-0">
          {{state}}
          <div class="col-12 col-md-6 mb-3">
            <select id="state" class="form-control form-control-lg border-dark" required>
              <option value disabled selected hidden>State</option>
              <template v-for="item in nigeria">
                <option
                  :key="item.state.postalcode"
                  :value="item.state.name"
                >{{item.state.name}} / {{item.state.postalCode}}</option>
                {{state = item.state}}
              </template>
            </select>
          </div>
          <div class="col-12 col-md-6 mb-3">
            <select id="lga" class="form-control form-control-lg border-dark" required>
              <option value disabled selected hidden>L.G.A</option>
              <option
                v-for="lga in state.lga"
                :key="lga.postalcode"
                :value="lga.postalcode"
              >{{lga.name}} / {{lga.postalCode}}</option>
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
      state: "",
      lga: "",
      output: ""
    };
  }
};
</script>

<style>
.border,
.form-control {
  border-width: 2px !important;
}
</style>
