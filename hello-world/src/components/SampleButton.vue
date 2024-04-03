<template>
  <div>
    <button v-on:click="increment()">{{ButtonName}}</button>
  </div>
</template>

<script>

export default {
  name: 'SampleButton',
  // プロパティ定義
  props: {
        ButtonName: String,
        countNumber: Number,
    },
  methods: {
    increment(){
      this.$emit("return-number", this.countNumber + 1)
    }
  }
}

</script>

