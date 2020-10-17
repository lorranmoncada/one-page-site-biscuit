<template>
  <div class="container sobre">
    <v-row class="justify-center">
      <h1 id="about">Sobre</h1>
    </v-row>
    <v-row>
      <v-col
        ><div class="d-flex justify-center">
          <img
            src="@/assets/teste.png"
            style="border-radius: 148px;"
            height="300rem"
            alt="perfil"
          />
        </div>
      </v-col>
      <v-col class="mt-15"
        ><h3>
          Oi, me chamo Emmely Raissa, também conhecida como Mily biscuit! Sou
          artesã de Recife e trabalho com biscuit a 5 anos. Realizando pedidos
          com muito amor, carinho e dedicação.<br />
          Sejam bem vindos !!! <span>&#128525;</span>
        </h3></v-col
      >
    </v-row>
  </div>
</template>

<script>
import ScrollReveal from "scrollreveal";
export default {
  name: "Sobre",
  /*  components: {
    HelloWorld
  } */

  mounted() {
    ScrollReveal({ reset: true });
    const sr = ScrollReveal({
      origin: "top",
      distance: "80px",
      duration: 2000,
      reset: true
    });

    sr.reveal(".sobre", {});
  }
};
</script>

<style lang="scss">
#about::after {
  position: absolute;
  content: "";
  width: 7.7rem;
  height: 0.18rem;
  margin-left: 7px;
  border-radius: 30px;
  background-color: tomato;
  margin-top: -1rem;
  display: flex;
  justify-content: center;
}
</style>