 <template>
  <section class="container contato">
    <v-row class="justify-center">
      <h1>Contato</h1>
    </v-row>
    <div class="background">
      <form class="form" @submit.prevent="sendEmail">
        <v-row class="justify-center">
          <h2 class="titulo-form">
            Mande-nos um e-mail, ficaremos felizes em atende-los!
          </h2>
        </v-row>
        <v-row justify="center"
          ><input
            type="text"
            placeholder="Nome"
            name="name"
            class="form-nome mb-4"/></v-row
        ><v-row justify="center"
          ><input
            type="number"
            placeholder="Telefone"
            name="telephone"
            class="form-nome mb-4"
        /></v-row>
        <v-row justify="center"
          ><input
            name="email"
            type="email"
            placeholder="Email"
            class="form-email mb-4"/></v-row
        ><v-row justify="center"
          ><textarea
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
            Normal
          </v-btn>
        </v-row>
      </form>
    </div>
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
      origin: "bottom",
      distance: "80px",
      duration: 2000,
      reset: true
    });

    sr.reveal(".contato", {});
  }
};
</script>

<style lang="scss" scoped>
::-webkit-input-placeholder {
  color: white;
}

.background {
  background: url(../assets/subscribe-bg.png) no-repeat;
  padding: 17rem 0;
  border-radius: 10px;
}
.form-nome {
  width: 40%;
  border: 2px solid #fff;
  height: 42px;
  background-color: #6b53e7;
  border-radius: 5px;
  color: white !important;
}

.form-text-area {
  width: 40%;
  border: 2px solid #fff;
  background-color: #6b53e7;
  border-radius: 5px;
  color: white !important;
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
  color: #efefef;
}

@media screen and (max-width: 500px) {
  h2 {
    font-size: 25px;
  }
}
</style>