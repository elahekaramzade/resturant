<template>
  <header class>
    <div class="container-fluid red">
      <div class="row justify-content-center pt-3">
        <div class="col-xs-2">
          <div class="logo-box text-center">
            <img src="../assets/wheat.png" width="50" alt />
            <p>
              <strong>Resturant Menu</strong>
            </p>
          </div>
        </div>
      </div>
      <div class="row justify-content-center">
        <div class="col-sm-10">
          <div class="col-auto">
            <label class="sr-only" for="inlineFormInputGroup">what do you want to eat...</label>
            <div class="input-group mb-3">
              <input
                type="text"
                class="form-control br-0"
                id="inlineFormInputGroup"
                placeholder="what do you want to eat..."
              />
              <div class="input-group-append bl-0">
                <div class="input-group-text">
                  <a>
                    <span class="icon-search"></span>
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {};
</script>

<style>
.red {
  background: #e13548;
}
.p-0 {
  padding: 0 !important;
}
.bl-0 {
  border-left: none;
}
.br-0 {
  border-right: none;
}
</style>