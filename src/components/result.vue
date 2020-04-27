<template>
    <ion-content id="result">

        {{result[0]}} {{result[1]}}

    </ion-content>
</template>

<script>
  export default {
    name: "result",
    props: {
      result: Array
    }
  }
</script>
