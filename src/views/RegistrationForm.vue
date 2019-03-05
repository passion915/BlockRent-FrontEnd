<template>
  <v-form>
    <p class="font-weight-bold text-xs-center">
      Register your security deposit application<br />
      by filling out the form below
    </p>
    <v-container>
      <h1>Tenant details:</h1>
      <div class="section">
        <v-layout row wrap>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="personalDetails.firstName"
              :rules="nameRules"
              label="First name"
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="personalDetails.lastName"
              :rules="nameRules"
              label="Last name"
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="personalDetails.phoneNumber"
              :rules="phoneNumberRules"
              label="Phone number"
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field v-model="personalDetails.email" :rules="emailRules" label="Email" required></v-text-field>
          </v-flex>
        </v-layout>
      </div>
    </v-container>
    <v-container>
      <h1>Lease Application details:</h1>
      <div class="section">
        <v-layout row wrap>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="leaseApplicationDetails.contractNo"
              :rules="contractNoRules"
              label="Ejari Contract/Certificate No."
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="leaseApplicationDetails.contractStartDate"
              :rules="dateRules"
              label="Lease Contract Start Date"
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="leaseApplicationDetails.address"
              :rules="addressRules"
              label="Property Address"
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="leaseApplicationDetails.contractEndDate"
              :rules="dateRules"
              label="Lease Contract End Date"
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="leaseApplicationDetails.securityDepositAmount"
              :rules="emailRules"
              label="Security Deposit Amount"
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="leaseApplicationDetails.premiseNo"
              :rules="premiseNoRules"
              label="Premise No. (DEWA)"
              required
            ></v-text-field>
          </v-flex>
        </v-layout>
      </div>
    </v-container>
    <v-container>
      <h1>Landlord/owner details:</h1>
      <div class="section">
        <v-layout row wrap>
          <v-flex xs12 sm6>
            <v-text-field v-model="otherParty.firstName" :rules="nameRules" label="First name" required></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field v-model="otherParty.lastName" :rules="nameRules" label="Last name" required></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field
              v-model="otherParty.phoneNumber"
              :rules="phoneNumberRules"
              label="Phone number"
              required
            ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
            <v-text-field v-model="otherParty.email" :rules="emailRules" label="Email" required></v-text-field>
          </v-flex>
        </v-layout>
      </div>
    </v-container>
    <v-container mt-3>
      <v-layout row>
        <span class="company-name">BlockRent.io</span>
        <v-spacer class="hidden-sm-and-down"></v-spacer>
        <v-btn class="primary--text" color="secondary" to="/" large>Cancel</v-btn>
        <v-btn class="secondary--text" color="primary" @click="submit" large>Submit</v-btn>
      </v-layout>
    </v-container>
  </v-form>
</template>

<script>
// import axios from 'axios'

export default {
  name: 'RegistrationForm',
  data() {
    return {
      valid: false,
      personalDetails: {
        firstName: '',
        lastName: '',
        phoneNumber: '',
        email: ''
      },
      leaseApplicationDetails: {
        contractNo: '',
        contractStartDate: '',
        contractEndDate: '',
        address: '',
        premiseNo: '',
        securityDepositAmount: ''
      },
      otherParty: {
        firstName: '',
        lastName: '',
        phoneNumber: '',
        email: ''
      },
      nameRules: [v => !!v || 'Name is required'],
      phoneNumberRules: [v => !!v || 'Phone number is required'],
      emailRules: [v => !!v || 'E-mail is required', v => /.+@.+/.test(v) || 'E-mail must be valid'],
      dateRules: [v => !!v || 'Date is required'],
      addressRules: [v => !!v || 'Address is required'],
      contractNoRules: [v => !!v || 'Ejari Contract/Certificate No. is required'],
      premiseNoRules: [v => !!v || 'Premise No.(DEWA) is required']
    }
  },
  methods: {
    async submit() {
      console.log('Submitting...')
      console.log({
        registrationForm: {
          personalDetails: this.personalDetails,
          leaseApplicationDetails: this.leaseApplicationDetails,
          otherParty: this.otherParty
        }
      })

      // const response = await axios.post('206.189.209.201:8000/api/v1/registrations', {
      //   registrationForm: {
      //     personalDetails: this.personalDetails,
      //     leaseApplicationDetails: this.leaseApplicationDetails,
      //     otherParty: this.otherParty
      //   }
      // })
      //
      // console.log(response)

      this.$router.push('thanks')
    }
  }
}
</script>

<style scoped>
h1 {
  color: var(--v-primary-base);
  margin-bottom: 1rem;
}
p {
  font-size: 1.5rem;
}
.section {
  border: 2px solid var(--v-primary-base);
  padding: 1rem;
}
.company-name {
  font-size: 2rem;
  font-weight: bold;
  color: var(--v-primary-base);
}
</style>
