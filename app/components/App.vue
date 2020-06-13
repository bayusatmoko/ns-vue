<template>
    <Page>
        <StackLayout>
            <TextField type="number" class="message" v-model="firstNumber" hint="Masukkan angka ..." />
            <TextField type="number" class="message" v-model="secondNumber" hint="Masukkan angka ..." />
            <Button @tap="sum">Jumlahkan</Button>
            <TextField disabled v-model="sumResult" class="message" />
        </StackLayout>
    </Page>
</template>

<script >
  export default {
    data() {
      return {
          firstNumber: null,
          secondNumber: null,
          sumResult: null
      }
    },
      methods: {
        sum () {
            if(this.firstNumber === null || this.secondNumber === null) {
                return alert('Silahkan isi angka!')
            }
            alert('Berhasil menjumlahkan!')
            this.sumResult = parseInt(this.firstNumber) + parseInt(this.secondNumber)
        }
      },
      computed: {
        result () {
            return parseInt(this.firstNumber) + parseInt(this.secondNumber)
        }
      }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: middle;
        text-align: left;
        font-size: 12px;
        font-style: normal;
        color: #333333;
    }
</style>
