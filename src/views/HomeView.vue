<template>
  <div class="">
    <div class="text-2xl font-bold">Number Guessing Game</div>
    <div class="">Guess a number between 10 and 99!</div>
    <div v-if="resultStatus" class="border p-3 border-blue-500 rounded" style="margin: 5px">
      <div>{{ resultStatus }}</div>
      <div>Your Number is {{ myNum }} | Ramdom Number is {{ randomNum }}</div>
    </div>
    <div class="flex gap-2 item-center">
      <div class="flex flex-col">
        <input
          placeholder="Enter number..."
          type="number"
          v-model="num"
          class="border p-2 rounded"
        />
      </div>
      <button @click="submitBtn()" class="bg-blue-500 hover:bg-blue-400 p-2 text-white rounded">
        submit
      </button>
    </div>
    <div>
      <small v-if="validate" class="text-red-500">{{ validate }}</small>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num: '',
      myNum: '',
      randomNum: '',
      validate: '',
      resultStatus: '',
    }
  },
  methods: {
    submitBtn() {
      if (this.num == '') {
        return (this.validate = 'Number must be fill')
      }

      if (this.num < 10) {
        return (this.validate = 'Number must be 2 character')
      }
      if (this.num > 99) {
        return (this.validate = 'Number must be 2 character')
      }
      if (this.num === this.randomNum) {
        this.validate = ''
        this.resultStatus = 'You Win !'
        this.myNum = this.num
        this.randomNum = Math.floor(Math.random() * 100)
        this.num = ''

        return
      } else {
        this.validate = ''
        this.resultStatus = 'You Lose !'
        this.myNum = this.num
        this.randomNum = Math.floor(Math.random() * 100) + 1
        this.num = ''
        return
      }
    },
  },
}
</script>

<style lang="stylus" scoped></style>
