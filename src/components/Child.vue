
<template>
  <div>
    <h1> {{ name }} </h1>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      // type: String,
      required: true,
      // default: 'Pass in a string dummy!'
      validator(val){
        let types = ['string', 'number'];
        return types.includes(typeof val);
      }
    }
  }
}
</script>

