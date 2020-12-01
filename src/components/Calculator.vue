<template>
  <v-app>
    <div class="d-flex justify-center">
      <div class="container">
        <div class="header">
          <p>Mortgage Calculator</p>
          <v-icon size="36" color="#525252"> mdi-close </v-icon>
        </div>
        <div class="sub-header">
          <div>$2,242 per month</div>
          <div>
            <a class="d-flex align-center justify-center"
              >30-Year Fixed, 4.25% interest
              <img class="ml-2" src="./../icons/Icon1.svg" />
            </a>
          </div>
        </div>
        <div class="wrapper-ppcd">
          <v-form>
            <v-layout column wrap>
              <v-flex xs12 sm6 md3>
                <label class="label-heading" for="PurchasePrice"
                  >Purchase Price</label
                >
                <v-text-field
                  v-model="purchasePrice"
                  outlined
                  color="#57C1A6"
                  class="inputField"
                  ><v-icon size="19" slot="prepend-inner" color="#57C1A6"
                    >mdi-currency-usd</v-icon
                  >
                </v-text-field>
              </v-flex>
              <v-flex xs12 sm6 md3>
                <label class="label-heading" for="CashDown"
                  >Cash down
                  <img class="ml-2" src="./../icons/Icon1.svg" />
                </label>
                <div class="d-flex">
                  <v-text-field class="left-input" outlined v-model="cashDown"
                    ><v-icon size="19" slot="prepend-inner" color="#57C1A6"
                      >mdi-currency-usd</v-icon
                    >
                    ></v-text-field
                  >
                  <v-text-field class="right-input" outlined v-model="percent"
                    ><v-icon size="19" slot="append" color="#57C1A6"
                      >mdi-percent</v-icon
                    ></v-text-field
                  >
                </div>
              </v-flex>
            </v-layout>
          </v-form>
        </div>
        <div class="loan-term">
          <v-form>
            <v-layout column wrap>
              <v-flex xs12 sm6 md3>
                <label for="PurchasePrice" class="label-heading"
                  >Loan term
                  <img class="ml-2" src="./../icons/Icon1.svg" />
                </label>
                <v-combobox
                  class="loan-term-input"
                  outlined
                  v-model="loanTerm"
                  :items="loanTerms"
                ></v-combobox>
              </v-flex>
              <v-flex xs12 sm6 md3>
                <label for="InterestRate" class="label-heading"
                  >Interest rate
                  <img class="ml-3" src="./../icons/Icon1.svg" />
                </label>
                <v-text-field
                  class="loan-term-input"
                  outlined
                  v-model="interestRate"
                  ><v-icon size="19" slot="append" color="#57C1A6"
                    >mdi-percent</v-icon
                  ></v-text-field
                >
              </v-flex>
              <v-flex xs12 sm6 md3>
                <label for="CreditScore" class="label-heading"
                  >Credit score
                  <img class="ml-3" src="./../icons/Icon1.svg" />
                </label>
                <v-combobox
                  class="loan-term-input"
                  outlined
                  v-model="creditScore"
                  :items="creditScores"
                ></v-combobox>
              </v-flex>
            </v-layout>
          </v-form>
        </div>
        <div class="estimate-values">
          <span><h5>We estimated these values for you. Feel free to</h5></span>
          <v-form>
            <v-layout column wrap>
              <v-flex xs12 sm6 md3>
                <label for="PropertyTaxes" class="label-heading"
                  >Property taxes
                  <img class="ml-2" src="./../icons/Icon1.svg" />
                </label>
                <v-text-field
                  class="loan-term-input"
                  outlined
                  suffix="/month"
                  v-model="propertyTax"
                  ><v-icon size="19" slot="prepend-inner" color="#57C1A6"
                    >mdi-currency-usd</v-icon
                  ></v-text-field
                >
              </v-flex>
              <v-flex xs12 sm6 md3>
                <label for="HomeownerInsurance" class="label-heading"
                  >Homeowner insurance
                  <img class="ml-2" src="./../icons/Icon1.svg" />
                </label>
                <v-text-field
                  class="loan-term-input"
                  outlined
                  suffix="/month"
                  v-model="homeownerInsurance"
                  ><v-icon size="19" slot="prepend-inner" color="#57C1A6"
                    >mdi-currency-usd</v-icon
                  ></v-text-field
                >
              </v-flex>
              <v-flex xs12 sm6 md3>
                <label for="HOAdues" class="label-heading"
                  >HOA dues
                  <img class="ml-2" src="./../icons/Icon1.svg" />
                </label>
                <v-text-field
                  class="loan-term-input"
                  outlined
                  suffix="/month"
                  v-model="hoaDue"
                  ><v-icon size="19" slot="prepend-inner" color="#57C1A6"
                    >mdi-currency-usd</v-icon
                  ></v-text-field
                >
              </v-flex>
            </v-layout>
          </v-form>
        </div>
        <div class="action-buttons">
          <button class="get-pre-approved">Get Pre-approved</button>
          <button class="save-details">Save details</button>
        </div>
      </div>
    </div>
  </v-app>
</template>
<script>
export default {
  name: "Calculator",

  data() {
    return {
      purchasePrice: "280000",
      percent: null,
      cashDown: null,
      loanTerm: ["30-Year Fixed"],
      loanTerms: ["30-Year Fixed", "15-Year Fixed", "7/1 ARM", "5/1 ARM"],
      interestRate: "3.375",
      creditScore: "700+ Credit Score",
      creditScores: [
        "540+ Credit Score",
        "560+ Credit Score",
        "580+ Credit Score",
        "600+ Credit Score",
        "700+ Credit Score",
        "800+ Credit Score",
        "820+ Credit Score",
        "840+ Credit Score",
      ],
      propertyTax: "239",
      homeownerInsurance: "58",
      hoaDue: "250",
    };
  },
  watch: {
    percent(val) {
      this.cashDown = (this.purchasePrice * val) / 100;
    },
    purchasePrice(val) {
      this.cashDown = (val * this.percent) / 100;
    },
  },
  mounted() {
    this.percent = 10;
  },
};
</script>
<style scoped>
@font-face {
  font-family: "MontserratRegular";
  src: url("~@/fonts/montserrat-v15-latin-regular.woff");
}
* {
  font-family: MontserratRegular;
}
.container {
  position: absolute;
  max-width: 375px;
  border: 1px solid #c7c7c7;
}

.header {
  padding-top: 30px;
  display: flex;
  justify-content: space-between;
  align-items: self-start;
}

.header p {
  font-size: 24px;
  color: #1a545d;
  font-weight: bold;
}

.sub-header {
  margin: 14px 0px;
  padding: 12px 2px;
  background-color: #1a545d;
  text-align: center;
}

.sub-header div {
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  margin-bottom: 10px;
}

.sub-header a {
  color: #ffffffb3;
  font-weight: light;
  font-size: 14px;
}

.wrapper-ppcd {
  margin-left: 5px;
  margin-right: 5px;
  margin-top: 28px;
}

.label-heading {
  font-weight: 600;
  display: flex;
}

.wrapper-ppcd label {
  color: #393939;
}

.left-input {
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
  border-top-right-radius: 0px;
  border-bottom-right-radius: 0px;
}

.right-input {
  border-top-left-radius: 0px;
  border-bottom-left-radius: 0px;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
  width: 102px;
}

.v-text-field.v-text-field--enclosed {
  margin-top: 12px;
}

>>> .v-input input {
  font-weight: light;
  font-size: 14px;
}

>>> .v-text-field__suffix {
  color: #a0a0a0;
  font-size: 14px;
}

.loan-term {
  background-color: #f7f7f7;
  padding: 30px 15px;
  padding-bottom: 10px;
}

.loan-term-input {
  margin-top: 12px;
  width: 219px;
}

.estimate-values {
  background-color: #57c1a614;
  padding: 30px 28px;
  padding-bottom: 24px;
  margin-top: 15px;
  margin-bottom: 20px;
}

.estimate-values h5 {
  color: #525252;
  font-size: 12px;
  font-weight: lighter;
  margin-bottom: 17px;
}

.v-text-field__suffix {
  color: #a0a0a0;
  font-weight: lighter;
  font-size: 14px;
}

.action-buttons {
  display: inline-flex;
}

.action-buttons button {
  margin: 8px;
  border-radius: 45px;
  padding: 11px 23px;
  font-size: 15px;
  box-shadow: #0000001a 0px 3px 6px;
  opacity: 100%;
}

.action-buttons button:hover {
  box-shadow: #0000001a 0px 3px 6px;
}

.get-pre-approved {
  background-color: #1a545d;
  color: #fff;
}

.get-pre-approved:hover {
  background-color: #144148;
}

.save-details {
  background-color: #fde76c;
  color: #17424a;
}

.save-details:hover {
  background-color: #f8e36c;
  color: #14424a;
}
</style>
