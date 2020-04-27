<template>
    <div class="ion-page">
        <ion-header>
            <ion-toolbar>
                <ion-title>Currency converter</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding">
            <fixerForm v-on:result="getResult($event)"></fixerForm>
            <result v-bind:result="result"></result>
        </ion-content>
    </div>
</template>

<script>
  import fixerForm from "@/components/form"
  import result from "@/components/result"

  export default {
    name: "home",
    components: {
      'fixerForm': fixerForm,
      'result': result
    },
    data() {
      return {
        result: [
                'Resultat',
                ''
        ]
      }
    }
    ,
    methods: {
      getResult: function (result) {
        this.result = result
      }
    }
  }
</script>