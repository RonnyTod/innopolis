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
    methods: {
      validate (caller, called) {
        if (caller && called) {
          console.log(`id ${ caller.id }`, `called id ${ called.id }`);
        }

        this.getChildren((p, i) => i.validate(p, i), called);
      },

      getChildren (func, instance = this, rootInstance = this) {
        for (const childInstance of instance.$children) {
          if (rootInstance.$options.name === childInstance.$options.name) {
            func(rootInstance, childInstance);
          } else {
            rootInstance.getChildren(func, childInstance, rootInstance);
          }
        }
      }
    }
  };
</script>

<style scoped>

</style>