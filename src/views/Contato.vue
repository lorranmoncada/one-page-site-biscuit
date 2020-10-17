 <template>
  <section class=" contato">
    <v-row class="justify-center">
      <h1>Contato</h1>
      <!-- <div id="emmy-sub">
          <span id="sublinhado"></span>
        </div> -->
    </v-row>
    <div class="contact1">
      <div class="container-contact1">
        <div class="contact1-pic js-tilt" data-tilt>
          <img class="imagem-envio" src="../assets/testes.png" alt="IMG" />
        </div>

        <form @submit.prevent="sendEmail" class="contact1-form validate-form">
          <span class="contact1-form-title">
            Mande-nos um e-mail, ficaremos felizes em atende-los!
          </span>

          <div class="wrap-input1 ">
            <input
              class="input1"
              type="text"
              required
              name="name"
              placeholder="Name"
            />
            <span class="shadow-input1"></span>
          </div>

          <div class="wrap-input1 ">
            <input
              required
              class="input1"
              type="email"
              name="email"
              placeholder="Email"
            />
            <span class="shadow-input1"></span>
          </div>

          <div class="wrap-input1 ">
            <input
              required
              class="input1"
              type="number"
              name="telephone"
              placeholder="Telefone"
            />
            <span class="shadow-input1"></span>
          </div>

          <div class="wrap-input1 ">
            <textarea
              required
              class="input1"
              name="message"
              placeholder="Message"
            ></textarea>
            <span class="shadow-input1"></span>
          </div>

          <div class="container-contact1-form-btn">
            <button type="submit" class="contact1-form-btn">
              <span class="mt-7">
                Enviar E-mail
                <i class="fa fa-long-arrow-right" aria-hidden="true"></i>
              </span>
            </button>
          </div>
        </form>
      </div>
    </div>

    <!-- <div class="background">
      <form class="form" @submit.prevent="sendEmail">
        <v-row class="justify-center">
          <h2 class="titulo-form">
            Mande-nos um e-mail, ficaremos felizes em atende-los!
          </h2>
        </v-row>
        <v-row justify="center"
          ><input
            required
            type="text"
            placeholder="Nome"
            name="name"
            class="form-nome mb-4"/></v-row
        ><v-row justify="center"
          ><input
            required
            type="number"
            placeholder="Telefone"
            name="telephone"
            class="form-nome mb-4"
        /></v-row>
        <v-row justify="center"
          ><input
            required
            name="email"
            type="email"
            placeholder="Email"
            class="form-email mb-4"/></v-row
        ><v-row justify="center"
          ><textarea
            required
            name="message"
            placeholder="Ecreva-nos uma breve descrição do que você precisa :)"
            class="form-text-area"
            id="story"
            rows="5"
            cols="33"
          ></textarea
        ></v-row>

        <v-row class="mt-3" justify="center">
          <v-btn type="submit" depressed>
            Enviar
          </v-btn>
        </v-row>
      </form>
    </div> -->
  </section>
</template>


<script>
import ScrollReveal from "scrollreveal";
import emailjs from "emailjs-com";
export default {
  data() {
    return {
      rules: [
        value => !!value || "Required.",
        value => (value || "").length <= 20 || "Max 20 characters",
        value => {
          const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
          return pattern.test(value) || "Invalid e-mail.";
        }
      ]
    };
  },
  methods: {
    sendEmail: e => {
      emailjs
        .sendForm(
          "gmail",
          "template_sfgrerd",
          e.target,
          "user_YiYnz3NGt2q6aWTBiVbvk"
        )
        .then(
          result => {
            console.log("SUCCESS!", result.status, result.text);
          },
          error => {
            console.log("FAILED...", error);
          }
        );
      e.target.reset();
    }
  },
  mounted() {
    const sr = ScrollReveal({
      origin: "top",
      distance: "80px",
      duration: 2000,
      reset: true
    });

sr.reveal(".contato", {});
    sr.reveal(".contact1-form-title", {});
  }
};
</script>

<style lang="scss" scoped>
textarea {
  outline: none;
  border: none;
}

textarea:focus,
input:focus {
  border-color: transparent !important;
}

input::-webkit-input-placeholder {
  color: #999999;
}
input:-moz-placeholder {
  color: #999999;
}
input::-moz-placeholder {
  color: #999999;
}
input:-ms-input-placeholder {
  color: #999999;
}

textarea::-webkit-input-placeholder {
  color: #999999;
}
textarea:-moz-placeholder {
  color: #999999;
}
textarea::-moz-placeholder {
  color: #999999;
}
textarea:-ms-input-placeholder {
  color: #999999;
}

button {
  outline: none !important;
  border: none;
  background: transparent;
}

button:hover {
  cursor: pointer;
}

.contact1 {
  width: 100%;
  min-height: 100%;
  padding: 15px;

  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.container-contact1 {
  width: 1163px;
  background: #fff;
  border-radius: 10px;
  overflow: hidden;

  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;

  padding: 90px 130px 88px 148px;
}

.contact1-pic {
  width: 296px;
}

.contact1-pic img {
  max-width: 100%;
}

.contact1-form {
  width: 390px;
}

.contact1-form-title {
  display: block;
  font-family: "Chilanka", cursive !important;
  font-size: 24px;
  color: #333333;
  line-height: 1.2;
  text-align: center;
  padding-bottom: 44px;
}

input.input1 {
  height: 50px;
  border-radius: 25px;
  padding: 0 30px;
}
input.input1 + .shadow-input1 {
  border-radius: 25px;
}

textarea.input1 {
  min-height: 150px;
  border-radius: 25px;
  padding: 12px 30px;
}
textarea.input1 + .shadow-input1 {
  border-radius: 25px;
}

.wrap-input1 {
  position: relative;
  width: 100%;
  z-index: 1;
  margin-bottom: 20px;
}

.input1 {
  display: block;
  width: 100%;
  background: #e6e6e6;
  font-family: "Chilanka", cursive !important;
  font-size: 15px;
  line-height: 1.5;
  color: #666666;
}

.shadow-input1 {
  content: "";
  display: block;
  position: absolute;
  bottom: 0;
  left: 0;
  z-index: -1;
  width: 100%;
  height: 100%;
  box-shadow: 0px 0px 0px 0px;
  color: rgba(87, 184, 70, 0.5);
}

.input1:focus + .shadow-input1 {
  -webkit-animation: anim-shadow 0.5s ease-in-out forwards;
  animation: anim-shadow 0.5s ease-in-out forwards;
}

@-webkit-keyframes anim-shadow {
  to {
    box-shadow: 0px 0px 80px 30px;
    opacity: 0;
  }
}

@keyframes anim-shadow {
  to {
    box-shadow: 0px 0px 80px 30px;
    opacity: 0;
  }
}

.container-contact1-form-btn {
  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.contact1-form-btn {
  min-width: 193px;
  height: 50px;
  border-radius: 25px;
  background: #57b846;
  font-family: "Chilanka", cursive !important;
  font-size: 15px;
  line-height: 1.5;
  color: #fff;
  display: -webkit-box;
  display: -webkit-flex;
  display: -moz-box;
  display: -ms-flexbox;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 25px;

  -webkit-transition: all 0.4s;
  -o-transition: all 0.4s;
  -moz-transition: all 0.4s;
  transition: all 0.4s;
}

.contact1-form-btn i {
  margin-left: 7px;

  -webkit-transition: all 0.4s;
  -o-transition: all 0.4s;
  -moz-transition: all 0.4s;
  transition: all 0.4s;
}

.contact1-form-btn:hover {
  background: #333333;
}

.contact1-form-btn:hover i {
  -webkit-transform: translateX(10px);
  -moz-transform: translateX(10px);
  -ms-transform: translateX(10px);
  -o-transform: translateX(10px);
  transform: translateX(10px);
}

@media (max-width: 1200px) {
  .contact1-pic {
    width: 33.5%;
  }

  .contact1-form {
    width: 44%;
  }
}

@media (max-width: 992px) {
  .container-contact1 {
    padding: 90px 80px 88px 90px;
  }

  .contact1-pic {
    width: 35%;
  }

  .contact1-form {
    width: 55%;
  }
}

@media (max-width: 768px) {
  .container-contact1 {
    padding: 90px 80px 88px 80px;
  }

  .contact1-pic {
    display: none;
  }

  .contact1-form {
    width: 100%;
  }
}

@media (max-width: 576px) {
  .container-contact1 {
    padding: 90px 15px 88px 15px;
  }
}

.validate-input {
  position: relative;
}

.alert-validate::before {
  content: attr(data-validate);
  position: absolute;
  max-width: 70%;
  background-color: white;
  border: 1px solid #c80000;
  border-radius: 13px;
  padding: 4px 25px 4px 10px;
  top: 50%;
  -webkit-transform: translateY(-50%);
  -moz-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  -o-transform: translateY(-50%);
  transform: translateY(-50%);
  right: 8px;
  pointer-events: none;

  font-family: "Chilanka", cursive !important;
  color: #c80000;
  font-size: 13px;
  line-height: 1.4;
  text-align: left;

  visibility: hidden;
  opacity: 0;

  -webkit-transition: opacity 0.4s;
  -o-transition: opacity 0.4s;
  -moz-transition: opacity 0.4s;
  transition: opacity 0.4s;
}

.alert-validate::after {
  content: "\f06a";
  font-family: "Chilanka", cursive !important;
  display: block;
  position: absolute;
  color: #c80000;
  font-size: 15px;
  top: 50%;
  -webkit-transform: translateY(-50%);
  -moz-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  -o-transform: translateY(-50%);
  transform: translateY(-50%);
  right: 13px;
}

.alert-validate:hover:before {
  visibility: visible;
  opacity: 1;
}
::-webkit-input-placeholder {
  color: white;
}

.background {
  background: url(/img/subscribe-bg.32590a11.png) no-repeat;
  padding: 12rem 0;
  border-radius: 10px;
  margin-top: 4rem;
}
.form-nome {
  width: 40%;
  border: 2px solid #fff;
  height: 42px;
  background-color: #6b53e7;
  border-radius: 5px;
  color: white !important;
}

h1::after {
  position: absolute;
  content: "";
  width: 10.7rem;
  height: 0.18rem;
  margin-left: 7px;
  border-radius: 30px;
  background-color: tomato;
  margin-top: -1rem;
  display: flex;
  justify-content: center;
}

.form-text-area {
  width: 40%;
  border: 2px solid #fff;
  background-color: #6b53e7;
  border-radius: 5px;
  color: white !important;
}

/* #sublinhado {
  position: absolute;
  content: "";
  width: 6.7rem;
  height: 0.18rem;
  margin-left: -13px;
  border-radius: 30px;
  background-color: tomato;
} */

#emmy-sub {
  margin-bottom: 13px;
  margin-top: -9px;
  display: flex;
  justify-content: center;
}

textarea:focus,
input:focus,
select:focus {
  box-shadow: 0 0 0 0;
  border: 2px solid #fff;
  outline: 0;
}
.form {
  margin-top: -172px;
}

.form-email {
  width: 40%;
  border: 2px solid #fff;
  height: 42px;
  background-color: #6b53e7;
  border-radius: 5px;
  color: white !important;
}

input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

.titulo-form {
  position: absolute;
  margin-top: -60px;
  color: rgb(68 68 68);
}

@media screen and (max-width: 500px) {
  h2 {
    font-size: 25px;
  }
}
</style>