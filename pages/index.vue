<template>
  <div class="ph4 pv3 bg-washed-yellow vh-100">
    <nav class="pa3 pa4-ns">
      <a class="link dim black b f1-ns f3 tc db mb3 mb4-ns">Barcode Image Generator</a>
    </nav>
    <section class="center tc w-60-ns w-70">
      <button class="bg-white br3 pa3 ba dib tc" @click="generateRandomNumber"> Generate number: <span class=" bg-washed-red br3 pa2">{{number}}</span></button>
      <VueBarcode ref="barcode" :value="number" tag="img" format="CODE128" :options="options" class="db center tc mv3"></VueBarcode>
      <a class="dib bg-green pa3 br3 white" :href="link" download="ship label barcode">Download Barcode</a>
    </section>
  </div>
</template>

<script>
import VueBarcode from '@chenfengyuan/vue-barcode';
export default {
  components: {
    VueBarcode
  },
  data() {
    return {
      number: '111111',
      max: 100000000,
      min: 1000,
      tag: 'img',
      link: '',
      options: {
        width: 2.5,
        height: 150,
      },
    }
  },
  methods:{
    generateRandomNumber () {
      this.number = Math.floor(Math.random()*(this.max-this.min+1)+this.min);
      this.$nextTick(()=> {
        this.link = this.$refs.barcode.$el.src
      })
    },
  }
};
</script>
