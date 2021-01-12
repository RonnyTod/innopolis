<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "ValidateComponent",
    props: {
      id: {
        type: String,
        required: true
      }
    },
    provide () {
      return {
        parent: this
      };
    },
    inject: {
      parent: { default: undefined }
    },
    mounted () {
      if (this.parent?.$options.name === this.$options.name) {
        this.validate(this.parent, this);
      }
    },
    methods: {
      validate: (caller, called) => {
        console.log(`id ${ caller.id }`, `called id ${ called.id }`);
      }
    }
  };
</script>

<style scoped>

</style>