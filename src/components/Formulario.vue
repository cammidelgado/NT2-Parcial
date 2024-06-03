<template>

  <section class="src-components-formulario">
    <form @submit.prevent>
      <input type="text" v-model="entrada">
    </form>
    <br>

    <p>Cantidad caracteres = {{ contador }}</p>

    <p>1 - {{ codificado }} (codificado)</p>
    <p>2 - {{ mayuscula }} (mayuscula)</p>
    <p>3 - {{ minuscula }} (minuscula)</p>
    <p>4 - {{ mayusMin }} (mayuscula / minuscula)</p>
    <p>5 - {{ minMayus }} (minuscula / mayuscula)</p>



  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-formulario',
    props: [],
    mounted () {

    },
    data () {
      return {
        entrada: "",
      }
    },
    methods: {

    },
    computed: {

      codificado() {
        return this.entrada.toLowerCase().replace(/[aeiou]/g, (vocal) =>{
          switch (vocal){
            case 'a':
              return 'u'
            case 'e':
              return 'o'
            case 'o':
              return 'e'
            case 'u': 
              return 'a'
          }
        })
      },

      mayuscula() {
        return this.entrada.toUpperCase()
      },

      minuscula() {
        return this.entrada.toLowerCase()
      },

      mayusMin() {
        return [...this.entrada].map((char, index) =>
        index % 2 ? char.toLowerCase() : char.toUpperCase()
      ).join('')

      },

      minMayus() {
        return [...this.entrada].map((char, index) =>
        index % 2 ? char.toUpperCase() : char.toLowerCase()
      ).join('')
      },

      contador(){
        return this.entrada.length
      }

    }
}


</script>

<style scoped lang="css">
  
</style>
