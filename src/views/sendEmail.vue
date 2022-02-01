<template>
  <form class="email-form" @submit.prevent="onSubmit">
    <p>
        <label for="name"> Name:</label>
        <input id="name" v-model="name">
    </p>
    <p>
        <label for="phoneNumber"> Contact:</label>
        <input id="phoneNumber" type="number" v-model.number="phoneNumber">
    </p>
    <p>
        <label for="subject"> Subject:</label>
        <input id="subject" v-model="subject">
    </p>
    <p>
        <label for="mailContent"> Mail Content:</label>
        <textarea id="mailContent" v-model="mailContent"></textarea>
    </p>
    <p>
        <input id="submitButton" type="submit" value="submit">
    </p>
  </form>
</template>

<script>
export default {
  name: 'send-email',
  data () {
    return {
      name: '',
      subject: '',
      mailContent: '',
      phoneNumber: '',
      mailToSend: {},
      errorVals: []
    }
  },
  methods: {
    onSubmit () {
      this.mailToSend = {
        name: this.name,
        subject: this.subject,
        mailContent: this.mailContent,
        phoneNumber: this.phoneNumber
      }
      this.clearForm()
      console.log(this.mailToSend)
    },
    clearForm () {
      this.name = ''
      this.subject = ''
      this.mailContent = ''
      this.phoneNumber = ''
    }
  }
}
</script>

<style lang="scss">
#submitButton {
  background-color: #065eab;
  height: 35px;
  width: 115px;
  margin-right: 10px;
}
</style>
