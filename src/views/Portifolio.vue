 <template>
  <div class="container" id="overlay">
    <v-row class="justify-center">
      <h1>Portifolio</h1>
    </v-row>

    <v-tabs v-model="tab" centered icons-and-text>
      <v-tabs-slider></v-tabs-slider>

      <v-tab href="#tab-1">
        Recentes
        <v-icon>mdi-history</v-icon>
      </v-tab>

      <v-tab href="#tab-2">
        Favoritos
        <v-icon>mdi-heart</v-icon>
      </v-tab>

      <v-tab href="#tab-3">
        Todos
        <v-icon>mdi-account-box</v-icon>
      </v-tab>
    </v-tabs>

    <v-tabs-items v-model="tab">
      <div v-if="tab == 'tab-1'">
        <v-tab-item value="tab-1">
          <v-sheet class="mx-auto" max-width="1000">
            <v-slide-group v-model="model" class="pa-4" mandatory show-arrows>
              <v-slide-item
                v-for="(item, n) in recentes"
                :key="n"
                v-slot:default="{}"
              >
                <v-card
                  color="grey lighten-1"
                  class="ma-4"
                  height="200"
                  width="200"
                >
                  <v-row class="fill-height" align="center" justify="center">
                    <img
                      @click="setOverlay(item)"
                      class="testando"
                      :src="getImage(item)"
                      height="200rem"
                      width="200rem"
                      alt="perfil"
                    />
                  </v-row>
                </v-card>
              </v-slide-item>
            </v-slide-group>
          </v-sheet>
        </v-tab-item>
      </div>

      <div v-if="tab == 'tab-2'">
        <v-tab-item value="tab-2">
          <v-sheet class="mx-auto" max-width="1000">
            <v-slide-group v-model="model" class="pa-4" mandatory show-arrows>
              <v-slide-item
                v-for="(item, n) in favoritos"
                :key="n"
                v-slot:default="{}"
              >
                <v-card
                  color="grey lighten-1"
                  class="ma-4"
                  height="200"
                  width="200"
                >
                  <v-row class="fill-height" align="center" justify="center">
                    <img
                      @click="setOverlay(item)"
                      class="testando"
                      :src="getImage(item)"
                      height="200rem"
                      width="200rem"
                      alt="perfil"
                    />
                  </v-row>
                </v-card>
              </v-slide-item>
            </v-slide-group>
          </v-sheet>
        </v-tab-item>
      </div>

      <div v-if="tab == 'tab-3'">
        <v-tab-item value="tab-3">
          <v-sheet class="mx-auto" max-width="1000">
            <v-slide-group v-model="model" class="pa-4" mandatory show-arrows>
              <v-slide-item
                v-for="(item, n) in todos"
                :key="n"
                v-slot:default="{}"
              >
                <v-card
                  color="grey lighten-1"
                  class="ma-4"
                  height="200"
                  width="200"
                >
                  <v-row class="fill-height" align="center" justify="center">
                    <img
                      @click="setOverlay(item)"
                      class="testando"
                      :src="getImage(item)"
                      height="200rem"
                      width="200rem"
                      alt="perfil"
                    />
                  </v-row>
                </v-card>
              </v-slide-item>
            </v-slide-group>
          </v-sheet>
        </v-tab-item>
      </div>
    </v-tabs-items>

    <v-row justify="center">
      <v-overlay z-index="5" :value="lay">
        <img :src="clickImg" height="400rem" width="400rem" alt="perfil" />
      </v-overlay>
    </v-row>
  </div>
</template>


<script>
export default {
  data() {
    return {
      lay: null,
      clickImg: null,
      confirmLay: 0,
      model: null,
      tab: "tab-3",
      recentes: [
        { img: "../assets/11.png" },
        { img: "../assets/12.png" },
        { img: "../assets/13.png" },
        { img: "../assets/14.png" },
        { img: "../assets/15.png" }
      ],
      favoritos: [
        { img: "../assets/16.png" },
        { img: "../assets/17.png" },
        { img: "../assets/18.png" },
        { img: "../assets/19.png" },
        { img: "../assets/20.png" },
        { img: "../assets/21.png" },
        { img: "../assets/22.jpg" },
        { img: "../assets/23.jpg" },
        { img: "../assets/24.jpg" },
        { img: "../assets/25.jpg" }
      ],
      todos: [
        { img: "../assets/11.png" },
        { img: "../assets/12.png" },
        { img: "../assets/13.png" },
        { img: "../assets/14.png" },
        { img: "../assets/15.png" },
        { img: "../assets/16.png" },
        { img: "../assets/17.png" },
        { img: "../assets/18.png" },
        { img: "../assets/19.png" },
        { img: "../assets/20.png" },
        { img: "../assets/21.png" },
        { img: "../assets/22.jpg" },
        { img: "../assets/23.jpg" },
        { img: "../assets/24.jpg" },
        { img: "../assets/25.jpg" }
      ]
    };
  },
  methods: {
    setOverlay(item) {
      let corta = item.img.substring(10, 12);
      this.clickImg = item ? require("../assets/" + corta + ".png") : "";
      this.lay = true;
      this.confirmLay++;
    },
    getImage(item) {
      let corta = item.img.substring(10, 12);
      return item ? require("../assets/" + corta + ".png") : "";
    },
    setFalse() {
      this.lay = false;
    }
  },

  mounted() {
    let alias = this;
    let teste = document.querySelector("#overlay");
    teste.addEventListener("click", function() {
      if (alias.lay) {
        alias.confirmLay++;
      }

      if (alias.lay && alias.confirmLay != 2) {
        alias.setFalse();
        alias.confirmLay = 0;
      }
    });
  }
};
</script>

<style lang="scss" scoped>
.testando:hover {
  transform: scale(1.3);
  cursor: pointer;
}
</style>