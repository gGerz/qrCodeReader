<template>
  <div class="home">
    <h1>Welcome to the QR</h1>
    <button @click="openCamera">{{ isShowingCamera ? 'Exit' : 'Scan QE Code'}}</button>
    <qrcode-stream v-if="isShowingCamera" @decode="onDecode"></qrcode-stream>

    <h5>Полученный контент: <span v-html="qrContent"></span></h5>


    <h3>Some random QR</h3>
    <div class="qr-code-wrapper">
      <qrcode-vue
          :value="'idi nahuuuj'"
          :size="100"
      >
      </qrcode-vue>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import QrcodeVue from 'qrcode.vue'

@Component({
  components: {
    QrcodeVue
  },
  data () {
    return {
      qrContent: ''
    }
  }
})
export default class Home extends Vue {

  public isShowingCamera = false;

  public openCamera(): void {
    this.isShowingCamera = !this.isShowingCamera
  }

  public onDecode(decodedString: string) {
    console.log(this)

    if (decodedString) {
      this.qrContent = decodedString
    }
    console.log(decodedString)
  }
}
</script>

<style lang="scss">

</style>
