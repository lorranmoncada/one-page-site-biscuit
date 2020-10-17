<template>
  <div class="container">
    <v-row class="home">
      <v-col xs="6" md="6" sm="6" style="margin-top:6%;text-align: center;">
        <h1 class="h1">Olá Eu sou</h1>
        <h3 class="h2 text-uppercase">
          Mily
        </h3>
        <div id="emmy-sub">
          <span id="sublinhado"></span>
        </div>
        <h4 class="h4 text-uppercase">
          peças em biscuit e moldes de silicone!!!!
        </h4>
      </v-col>
      <v-col class="d-flex justify-center" xs="6" md="6" sm="6">
        <img
          width="650rem"
          src="../assets/emmy.png"
          alt="banner-img"
          class="img-fluid"
        />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ScrollReveal from "scrollreveal";
export default {
  name: "Home",
  /*  components: {
    HelloWorld
  } */

  mounted() {
    const sr = ScrollReveal({
      origin: "top",
      distance: "80px",
      duration: 2000,
      reset: true
    });

    sr.reveal(".home", {});
  }
};
</script>

<style lang="scss" scoped>
.h1 {
  font-size: 6rem !important;
  font-weight: 300;
  line-height: 6rem;
  letter-spacing: -0.015625em !important;
  font-family: "Chilanka", cursive !important;
}

.h2 {
  text-align: center;
  font-size: 3.75rem !important;
  font-weight: 300;
  line-height: 3.75rem;
  letter-spacing: -0.0083333333em !important;
  font-family: "Chilanka", cursive !important;
}

.h4 {
  font-size: 1.5rem !important;
  font-weight: 400;
  line-height: 2rem;
  letter-spacing: normal !important;
  font-family: "Chilanka", cursive !important;
}

#sublinhado {
  position: absolute;
  content: "";
  width: 6.7rem;
  height: 0.18rem;
  margin-left: -13px;
  border-radius: 30px;
  background-color: tomato;
}

#emmy-sub {
  margin-bottom: 13px;
  margin-top: -9px;
  display: flex;
  justify-content: center;
}
</style>


