<template>
  <div style="border: 1px solid red;">
    <p>
      Název ulice:
      <input v-model="nazevUlice" />
    </p>
    <p>
      Číslo popisné:
      <input v-model="cisloPopisne" />
    </p>
     <p>
      Číslo orientační:
      <input v-model="cisloOrientacni" />
    </p>
    
  </div>
</template>

<script>
export default {
  name: 'AdressEditor',
  data () {
    let regAddress = /^(.*) (\d*)([/]*)(\d*)$/.exec(this.value);

return {
 nazevUlice: regAddress[1] ? regAddress[1] : '',
 cisloPopisne: regAddress[2] ? regAddress[2] : '',
cisloOrientacni: regAddress[4] ? regAddress[4] : ''

  }
},

  props: {
    value: {
      type: String,
      default: 'Neznámá adresa 99/1'
    }
  },
  watch: {
    joinedAdress () {
      this.setFullAdress()
    },
   value () {
 let regAddress = /^(.*) (\d*)([/]*)(\d*)$/.exec(this.value);
     this.nazevUlice = regAddress[1] 
     this.cisloPopisne = regAddress[2]
      this.cisloOrientacni = regAddress[4]
 
    } 
  },
  computed: {
    joinedAdress () {
      let nazevCislo = [this.nazevUlice, this.cisloPopisne].filter((item) => item !== '').join(' ')
      let celaAdresa = [nazevCislo, this.cisloOrientacni].filter((item) => item !== '').join('/')
      return celaAdresa       
    }
  }, 
  methods: {
    setFullAdress () {
      this.$emit('input', this.joinedAdress)
    }
  }
}
</script>

<style scoped>

</style>
