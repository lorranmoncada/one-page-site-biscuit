<template>
  <v-app class="lorran">
    <div id="elemento">
      <nav color="teste" style="position:fixed;width:100%;" ref="nav">
        <v-row>
          <v-col>
            <h2 class="ml-5">
              <a href="#home"
                ><img
                  style="border-radius:50px;"
                  src="./assets/logo.jpg"
                  width="80rem"
                  height="80rem"
                  alt=""
              /></a></h2
          ></v-col>
          <v-col v-if="!isMobile">
            <v-row class="justify-end">
              <v-col v-for="(menu, href, index) in listaMenu" :key="index">
                <a
                  :href="menu.href"
                  style="text-decoration: none;"
                  class="black--text font"
                >
                  {{ menu.nome }}
                </a>
              </v-col>
            </v-row>
          </v-col>
          <v-col v-if="isMobile">
            <v-row class="justify-end">
              <v-menu
                rounded="lg"
                min-width="100%"
                transition="slide-y-transition"
              >
                <template v-slot:activator="{ on, attrs }">
                  <v-btn icon v-bind="attrs" v-on="on">
                    <v-app-bar-nav-icon class="icon"></v-app-bar-nav-icon>
                  </v-btn>
                </template>
                <v-list style="text-align:center;">
                  <v-list-item v-for="(menu, index) in listaMenu" :key="index">
                    <v-list-item-title class="black--text font"
                      ><a :href="menu.href" class="menu-font">{{
                        menu.nome
                      }}</a></v-list-item-title
                    >
                  </v-list-item>
                </v-list>
              </v-menu>
            </v-row>
          </v-col>
        </v-row>
      </nav>

      <v-main class="main">
        <div id="home">
          <home></home>
        </div>
        <div id="sobre">
          <sobre></sobre>
        </div>
        <div id="portifolio">
          <portifolio></portifolio>
        </div>
        <div id="contato">
          <contato></contato>
        </div>
      </v-main>
    </div>

     <footer class="footer-area" dark padless>
      <div class="container">
        <div class="">
          
          <v-card-title style="justify-content: center;">
            <strong>Siga-nos</strong>
            <v-btn v-for="(item, n) in icons" :key="n" class="mx-4" icon>
              <a :href="item.url" target="_blank" rel="noopener noreferrer"
                ><v-icon style="color:white;" size="24px">
                  {{ item.icon }}
                </v-icon></a
              >
            </v-btn>
          </v-card-title>
          <div class="copyrights text-center">
            <p class="para">
              Copyright © 2020 Todos os direitos reservados | Esse site foi
              feito por
              <a
                href="https://www.instagram.com/lorran.mendes/?hl=pt-br"
                target="_blanck"
                ><span style="color: white;"
                  ><strong> Lorran Mendes</strong></span
                ></a
              >
            </p>
          </div>
        </div>
      </div>
    </footer>
    <v-fab-transition>
      <v-btn key="mdi-share-variant" fab bottom left class="v-btn--example mb-3">
        <a
          href="https://wa.me/5581987772112?text=Olá%20Preciso%20de%20uma%20Consulta!"
          target="_blanck"
          ><img
            src="../src/assets/whatsapp.jpg"
            width="75px"
            style="margin-top: 3px; margin-right: 2px;"
            alt="whatsaap"
          />
        </a>
      </v-btn>
    </v-fab-transition>
  </v-app>
</template>

<script>
import Home from "./views/Home";
import Contato from "./views/Contato";
import Sobre from "./views/Sobre";
import Portifolio from "./views/Portifolio";

export default {
  name: "App",

  components: {
    Home,
    Sobre,
    Portifolio,
    Contato
  },

  data: () => ({
    icons: [
      {
        icon: "mdi-instagram",
        url: "https://www.instagram.com/mily_biscuit/?hl=pt-br"
      }
    ],
    listaMenu: [
      { nome: "Home", href: "#home" },
      { nome: "Sobre", href: "#sobre" },
      { nome: "Portifólio", href: "#portifolio" },
      { nome: "Contato", href: "#contato" }
    ],
    isMobile: false
  }),
  created() {
    this.listaMenu;
    this.isMobile = screen.width < 700;
    window.onscroll = () => {
      if (window.scrollY != 0) {
        this.$refs.nav.classList.remove("teste");
        this.$refs.nav.classList.add("nav-teste");

        screen.width < 700 ? (this.isMobile = true) : (this.isMobile = false);
        document.getElementById("elemento").click();
      } else {
        this.$refs.nav.classList.remove("nav-teste");
        this.$refs.nav.classList.add("teste");

        screen.width < 700 ? (this.isMobile = true) : (this.isMobile = false);
        document.getElementById("elemento").click();
      }
      /* this.$refs.nav.style.boxShadow = "0px 1px 32px slategrey";
      this.$refs.nav.style.backgournd = "#ffffff";
      this.$refs.nav.style.transition = "background 1s ease"; */
    };
  }
};
</script>

<style>
.menu-font {
  text-decoration: none;
  font-size: 40px;
}
.footer-area {
  background-color: #515151;
  color: #ffffff;
  /* padding: 5rem 0;
  background: url(./assets/footer-bg.png) no-repeat; */
}
a {
  text-decoration: none;
}
.v-btn--example {
  bottom: 0;
  position: fixed;
  margin: 0 0 16px 16px;
}
.nav-teste {
  background: #ffffff;
  box-shadow: 0px 1px 32px slategrey;
  z-index: 999;
  transition: background 1s ease;
  transition: box-shadow 1s ease;
}
.teste {
  box-shadow: 0px 0px 0px white;
  transition: box-shadow 1s ease;
}
.font {
  font-family: "Chilanka", cursive !important;
  font-size: 22px;
}
.main {
  margin-top: 9rem;
}
@media screen and (max-width: 536px) {
  .main {
    margin-top: 12rem;
  }
}

@media screen and (max-width: 500px) {
  .main {
    margin-top: 16rem;
    font-size: 30px;
  }
  .font {
    font-size: 20px;
  }
}

.menu {
  min-width: 360px;
  transform-origin: left top;
  text-align: center;
  z-index: 8;
  left: 0px;
}

@media screen and (max-width: 500px) {
  .lorran {
    width: 194%;
  }
}

@media screen and (max-width: 900px) {
  .lorran {
    width: "";
  }
}

.icon {
  margin-left: -6rem;
}
</style>
