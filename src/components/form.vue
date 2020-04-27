<template>
    <ion-list>
        <ion-item>
            <ion-input type="number" placeholder="EUR" v-on:change="number = $event.target.value"></ion-input>
        </ion-item>
        <ion-item>
            <ion-select @ionChange="currency = $event.target.value" placeholder="to">
                <ion-select-option v-for="(currency, acronym) in symbols" :key="currency" :value="acronym">{{ currency
                    }}
                </ion-select-option>
            </ion-select>
        </ion-item>
        <ion-item>
            <ion-button v-on:click="convert">Convert</ion-button>
        </ion-item>
    </ion-list>

</template>

<script>
  export default {
    name: "fixerform",
    data() {
      return {
        number: '',
        currency: '',
        symbols: ''
      }
    },
    methods: {
      convert: function () {
        fetch('http://data.fixer.io/api/latest?access_key=dd968fcd0e30cdf23aa7e56095c3a4bb&symbols=' + this.currency)
                .then(response => response.json())
                .then(json => this.push(json)
                )
      },
      push: function (json) {
        this.$emit('result', [json.rates[this.currency] * this.number, this.currency])
      }
    },
    mounted: function () {
      fetch('http://data.fixer.io/api/symbols?access_key=dd968fcd0e30cdf23aa7e56095c3a4bb')
              .then(response => response.json())
              .then(json => this.symbols = json.symbols)
    }
  }
</script>

<style scoped>

</style>