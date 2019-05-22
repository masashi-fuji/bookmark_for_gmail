<template>
  <section class="section">
    <h1 class="title">Gmail URI Generator</h1>
    <form id="form">
      <b-field label="To">
        <b-input v-model="to"></b-input>
      </b-field>
      <b-field label="CC">
        <b-input v-model="cc"></b-input>
      </b-field>
      <b-field label="BCC">
        <b-input v-model="bcc"></b-input>
      </b-field>
      <b-field label="Subject">
        <b-input v-model="subject"></b-input>
      </b-field>
      <b-field label="Body">
        <b-input v-model="body" type="textarea"></b-input>
      </b-field>
      <hr />
      <b-message title="Result">
        {{ gmailURI }}
      </b-message>
    </form>
  </section>
</template>

<script>
export default {
  data: function() {
    return {
      to: '',
      cc: '',
      bcc: '',
      subject: '',
      body: ''
    }
  },
  computed: {
    gmailURI: function() {
      return (
        'https://mail.google.com/mail/?view=cm&fs=1' +
        '&to=' +
        encodeURIComponent(this.to) +
        '&cc=' +
        encodeURIComponent(this.cc) +
        '&bcc=' +
        encodeURIComponent(this.bcc) +
        '&su=' +
        encodeURIComponent(this.subject) +
        '&body=' +
        encodeURIComponent(this.body)
      )
    }
  },
  methods: {
    generateURI() {
      this.$notification.open(this.subject)
    }
  }
}
</script>
