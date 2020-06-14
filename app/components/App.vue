<template>
    <Page>
        <StackLayout>
            <TextField type="number" class="message" v-model="firstNumber" hint="Masukkan angka ..." />
            <TextField type="number" class="message" v-model="secondNumber" hint="Masukkan angka ..." />
            <Button class="-primary -rounded-lg" @tap="sum">Jumlahkan</Button>
            <TextField disabled v-model="sumResult" class="message" />
            <Button class="-primary -rounded-lg" @tap="goToDetailPage">Navigate to Dashboard</Button>
        </StackLayout>
    </Page>
</template>

<script >
    import Dashboard from "./Dashboard";
    import axios from "axios";

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
             axios.post("http://127.0.0.1:3000/sum/", {
                 firstNumber: parseInt(this.firstNumber),
                 secondNumber: parseInt(this.secondNumber)
             }).then(result => {
                 this.sumResult = result.data.sum;
                 alert(result.data.message)
             }, error => {
                 console.error(error);
             });
        },
          goToDetailPage () {
              this.$navigateTo(Dashboard);
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
