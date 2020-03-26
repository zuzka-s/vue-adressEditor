<template>
  <div>

    <p>
      Adress:
      <input type="text" v-model="address">
    </p>
    <AdressEditor v-model="address" />

  </div>
</template>

<script>

/*
ÚKOL

Vytvorte komponentu AddressEditor pre editáciu adresy, ktorú dostanete vo formáte:
U garáží 1611/1

Chceme zvlášť políčka pre ulicu, číslo popisné, číslo orientačné.
*/

import AdressEditor from './AdressEditor'

export default {
  components: { AdressEditor },
  data: function () {
    return {
      address: 'U garáží 1611/1'
    }
  }
}
</script>

<style>

</style>
