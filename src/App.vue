<script setup>
</script>

<script>
export default {
  data() {
    return {
      name: "",
      cardNumber: "",
      expiration: "",
      cvv: "",
      zipCode: "",
    };
  },
  methods: {
    checkForm: function () {
      if (
        !this.name ||
        !this.cardNumber ||
        !this.expiration ||
        !this.cvv ||
        !this.zipCode
      ) {
        //return;
      }
      let tempCard = this.cardNumber.replace(/\D/g, "");

      let rejexCards = [
        /^3[47][0-9]{13}$/,
        /^(6541|6556)[0-9]{12}$/,
        /^389[0-9]{11}$/,
        /^3(?:0[0-5]|[68][0-9])[0-9]{11}$/,
        /^65[4-9][0-9]{13}|64[4-9][0-9]{13}|6011[0-9]{12}|(622(?:12[6-9]|1[3-9][0-9]|[2-8][0-9][0-9]|9[01][0-9]|92[0-5])[0-9]{10})$/,
        /^63[7-9][0-9]{13}$/,
        /^(?:2131|1800|35\d{3})\d{11}$/,
        /^9[0-9]{15}$/,
        /^(6304|6706|6709|6771)[0-9]{12,15}$/,
        /^(5018|5020|5038|6304|6759|6761|6763)[0-9]{8,15}$/,
        /^(5[1-5][0-9]{14}|2(22[1-9][0-9]{12}|2[3-9][0-9]{13}|[3-6][0-9]{14}|7[0-1][0-9]{13}|720[0-9]{12}))$/,
        /^(6334|6767)[0-9]{12}|(6334|6767)[0-9]{14}|(6334|6767)[0-9]{15}$/,
        /^(4903|4905|4911|4936|6333|6759)[0-9]{12}|(4903|4905|4911|4936|6333|6759)[0-9]{14}|(4903|4905|4911|4936|6333|6759)[0-9]{15}|564182[0-9]{10}|564182[0-9]{12}|564182[0-9]{13}|633110[0-9]{10}|633110[0-9]{12}|633110[0-9]{13}$/,
        /^(62[0-9]{14,17})$/,
        /^4[0-9]{12}(?:[0-9]{3})?$/,
        /^(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14})$/,
      ];

      let validCard = false;

      for (let i = 0; i < rejexCards.length || validType; i++) {
        if (rejexCards[i].test(tempCard)) {
          validCard = true;
          break;
        }
      }

      if (validCard) {
        this.name = "";
        this.cardNumber = "";
        this.expiration = "";
        this.cvv = "";
        this.zipCode = "";
      }

      console.log("Tarjeta Valida: ", validCard);

      // this.submitForm();
    },
  },
};
</script>


<template>
  <main>
    <div class="checkout">
      <p class="simbol">💰</p>
      <h1>Payment info</h1>
      <form action="" class="form" @submit.prevent="checkForm">
        <div class="form-group">
          <label for="name">Full Name</label>
          <input
            v-model="name"
            required
            type="text"
            name="name"
            id="name"
            class="form-control"
            placeholder="Your Name"
          />
        </div>

        <div class="form-group">
          <label for="cardNumber">Card Number</label>
          <input
            class="form-control py-2 border-right-0 border"
            v-model="cardNumber"
            required
            type="text"
            name="cardNumber"
            id="cardNumber"
            placeholder="1234 1234 1234 1234"
          />
          <span class="inputIcon">
            <i class="fa-solid fa-credit-card"></i>
          </span>
        </div>

        <div class="row">
          <div class="col">
            <label for="expiration">Expiration</label>
            <input
              v-model="expiration"
              required
              type="text"
              name="expiration"
              id="expiration"
              class="form-control"
              placeholder="MM/YY"
            />
          </div>
          <div class="col">
            <label for="cvv">CVV</label>
            <input
              v-model="cvv"
              required
              maxlength="3"
              type="text"
              name="cvv"
              id="cvv"
              class="form-control"
              placeholder="..."
            />
            <span class="inputIcon2">
              <i class="fa-solid fa-circle-info"></i>
            </span>
          </div>
        </div>

        <div class="form-group">
          <label for="zipCode">Zip Code</label>
          <input
            v-model="zipCode"
            required
            type="text"
            name="zipCode"
            id="zipCode"
            class="form-control"
            placeholder="Your Zip"
          />
        </div>

        <button type="submit" class="btn btn-primary">Confirm Payment</button>
        <p class="instruction">
          <small>You verify that this info is correct</small>
        </p>
      </form>
    </div>
  </main>
</template>

<style>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
.checkout {
  flex-direction: column;
  width: 319px;
  height: 607px;
  border-radius: 8px;
  padding: 32px;
  background: #ffffff;
  box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
}
.simbol {
  text-align: center;
  font-size: 4em;
}
.form {
  display: flex;
  flex-direction: column;
  gap: 1em;
}
.instruction {
  text-align: center;
}
.inputIcon {
  position: relative;
  top: -32px;
  left: 85%;
  color: #a7bac5;
}

.inputIcon2 {
  position: relative;
  top: -32px;
  left: 70%;
  color: #a7bac5;
}
</style>
