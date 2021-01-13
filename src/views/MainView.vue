<template>
  <ValidateComponent id="1">
    <SomeComponent>
      <ValidateComponent id="2"></ValidateComponent>
    </SomeComponent>
    <SomeComponent>
      <ValidateComponent id="3">
        <ValidateComponent id="4"></ValidateComponent>
        <ValidateComponent id="6">
          <SomeComponent>
            <ValidateComponent id="7"></ValidateComponent>
          </SomeComponent>
        </ValidateComponent>
      </ValidateComponent>
    </SomeComponent>
    <ValidateComponent id="5"></ValidateComponent>
  </ValidateComponent>
</template>

<script>
  import SomeComponent from "@/components/common/SomeComponent";
  import ValidateComponent from "@/components/common/ValidateComponent";

  export default {
    name: "MainView",
    components: { SomeComponent, ValidateComponent },
    mounted () {
      this.$children[0].validate();
    }
  };
</script>

<style scoped>

</style>