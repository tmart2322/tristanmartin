<template>
    <v-container fluid>
      <div class="display-3 text-center">Tristan's Wish List</div>
      <v-row dense>
        <v-col
                v-for="card in cards"
                :key="card.title"
                :cols="cols"
        >
          <v-card>
            <v-img
                    :src="card.src"
                    class="white--text align-end"
                    gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                    height="200px"
            >
              <v-card-title v-text="card.title"></v-card-title>
              <v-card-subtitle v-text="card.subtitle" class="color-white"></v-card-subtitle>
            </v-img>

            <v-card-actions>
              <v-spacer></v-spacer>

              <div v-for="link in card.links"
                   :key="card.title">
                <v-btn :href="link.link" target="_blank">{{link.text}}</v-btn>
              </div>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
</template>

<script>
  export default {
    data: () => ({
      windowWidth: 0,
      cards: [
        {
          title: 'Altimeter',
          subtitle: '$169',
          src: 'http://www.chutingstar.com/media/catalog/product/cache/1/image/1200x/040ec09b1e35df139433887a97daa66f/a/l/alti-2_galaxy_10.jpg',
          links: [
            {
              text: 'Chuting Star',
              link: 'http://www.chutingstar.com/altimaster-galaxy-altimeter'
            }
          ]
        },
        {
          title: 'Audible Altimeter',
          subtitle: '$332',
          src: 'http://www.chutingstar.com/media/catalog/product/cache/1/image/1200x/040ec09b1e35df139433887a97daa66f/o/p/optimaii_lrg_1_1.jpg',
          links: [
            {
              text: 'Chuting Star',
              link: 'http://www.chutingstar.com/optima-ii-audible-altimeter-visual-warning-port'
            }
          ]
        },
        {
          title: 'Skydiving Gift Card',
          subtitle: '$50/$100/$200',
          src: 'https://store.burblesoft.com/img/Image%20Library/Gift-Cards--Dollar-Icons-200.jpg',
          links: [
            {
              text: 'Burble',
              link: 'https://store.burblesoft.com/?dz_id=6743'
            }
          ]
        },
      ]
    }),

    computed: {
      cols: function() {
        if (this.windowWidth > 1200) {
          return 4;
        } else if (this.windowWidth > 900) {
          return 6;
        }
        return 12;
      }
    },

    mounted() {
      this.windowWidth = window.innerWidth;
      this.$nextTick(() => {
        window.addEventListener('resize', () => {
          this.windowWidth = window.innerWidth
        });
      })
    }
  }
</script>

<style scoped>
  .color-white {
    color: rgba(255, 255, 255, 1) !important;
  }
</style>
