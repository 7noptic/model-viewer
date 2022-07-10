<template>
  <div>
    <div class="info">
      <div class="info-block">
        <p class="info-block__title">
          bloomers
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="bloomers"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          boots
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="boots"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          burka
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="burka"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          camisole
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="camisole"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          cap
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="cap"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          cross
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="cross"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          earring
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="earring"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          pendant
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="pendant"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          sputnik
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="sputnik"
          @input="pushToArray"
        />
      </div>

      <div class="info-block">
        <p class="info-block__title">
          whip
        </p>
        <v-select
          item-text="name"
          item-value="last"
          class="info-block__select"
          :items="whip"
          @input="pushToArray"
        />
      </div>

    </div>
    <AppViewer
      :files-props="models"
    />
  </div>
</template>

<script>
import AppViewer from '@/components/AppViewer'

export default {
  components: {
    AppViewer
  },
  data: () => ({
    bloomers: [
      'models/BLOOMERS/COSSACK_BLOOMERS_1#40.glb',
      'models/BLOOMERS/COSSACK_BLOOMERS_2#30.glb',
      'models/BLOOMERS/COSSACK_BLOOMERS_3#20.glb',
      'models/BLOOMERS/COSSACK_BLOOMERS_4#10.glb'
    ],
    boots: [
      'models/BOOTS/COSSACK_BOOTS_1#40.glb',
      'models/BOOTS/COSSACK_BOOTS_2#30.glb',
      'models/BOOTS/COSSACK_BOOTS_3#20.glb',
      'models/BOOTS/COSSACK_BOOTS_4#10.glb'
    ],
    burka: [
      'models/BURKA/COSSACK_BURKA_1#40.glb',
      'models/BURKA/COSSACK_BURKA_2#30.glb',
      'models/BURKA/COSSACK_BURKA_3#20.glb',
      'models/BURKA/COSSACK_BURKA_4#10.glb'
    ],
    camisole: [
      'models/CAMISOLE/COSSACK_CAMISOLE_1#40.glb',
      'models/CAMISOLE/COSSACK_CAMISOLE_2#30.glb',
      'models/CAMISOLE/COSSACK_CAMISOLE_3#20.glb',
      'models/CAMISOLE/COSSACK_CAMISOLE_4#10.glb'
    ],
    cap: [
      'models/CAP/COSSACK_CAP_1#40.glb',
      'models/CAP/COSSACK_CAP_2#30.glb',
      'models/CAP/COSSACK_CAP_3#20.glb',
      'models/CAP/COSSACK_CAP_4#10.glb'
    ],
    cross: [
      'models/CROSS/COSSACK_CROSS_1#40.glb',
      'models/CROSS/COSSACK_CROSS_2#30.glb',
      'models/CROSS/COSSACK_CROSS_3#20.glb',
      'models/CROSS/COSSACK_CROSS_4#10.glb'
    ],
    earring: [
      'models/EARRING/COSSACK_EARRING_1#40.glb',
      'models/EARRING/COSSACK_EARRING_2#30.glb',
      'models/EARRING/COSSACK_EARRING_3#20.glb',
      'models/EARRING/COSSACK_EARRING_4#10.glb'
    ],
    pendant: [
      'models/PENDANT/COSSACK_PENDANT_1#40.glb',
      'models/PENDANT/COSSACK_PENDANT_2#30.glb',
      'models/PENDANT/COSSACK_PENDANT_3#20.glb',
      'models/PENDANT/COSSACK_PENDANT_4#10.glb'
    ],
    sputnik: [
      'models/SPUTNIK/COSSACK_SPUTNIK_1#40.glb',
      'models/SPUTNIK/COSSACK_SPUTNIK_2#30.glb',
      'models/SPUTNIK/COSSACK_SPUTNIK_3#20.glb',
      'models/SPUTNIK/COSSACK_SPUTNIK_4#10.glb'
    ],
    weapon: [
      'models/WEAPON/COSSACK_WEAPON_1#10.glb',
      'models/WEAPON/COSSACK_WEAPON_2#9.glb',
      'models/WEAPON/COSSACK_WEAPON_3#9.glb',
      'models/WEAPON/COSSACK_WEAPON_4#8.glb',
      'models/WEAPON/COSSACK_WEAPON_5#8.glb',
      'models/WEAPON/COSSACK_WEAPON_6#7.glb',
      'models/WEAPON/COSSACK_WEAPON_7#7.glb',
      'models/WEAPON/COSSACK_WEAPON_8#6.glb',
      'models/WEAPON/COSSACK_WEAPON_9#6.glb',
      'models/WEAPON/COSSACK_WEAPON_10#5.glb',
      'models/WEAPON/COSSACK_WEAPON_11#5.glb',
      'models/WEAPON/COSSACK_WEAPON_12#4.glb',
      'models/WEAPON/COSSACK_WEAPON_13#4.glb',
      'models/WEAPON/COSSACK_WEAPON_14#3.glb',
      'models/WEAPON/COSSACK_WEAPON_15#3.glb',
      'models/WEAPON/COSSACK_WEAPON_16#2.glb',
      'models/WEAPON/COSSACK_WEAPON_17#2.glb',
      'models/WEAPON/COSSACK_WEAPON_18#1.glb',
      'models/WEAPON/COSSACK_WEAPON_19#1.glb',
      'models/WEAPON/COSSACK_WEAPON_20#0.glb'
    ],
    whip: [
      'models/WHIP/COSSACK_WHIP_1#40.glb',
      'models/WHIP/COSSACK_WHIP_2#30.glb',
      'models/WHIP/COSSACK_WHIP_3#20.glb',
      'models/WHIP/COSSACK_WHIP_4#10.glb'
    ],
    models: []
  }),
  methods: {
    pushToArray (e) {
      setTimeout(this.getInfoSelect, 1000)

    },
    getInfoSelect () {
      const selects = document.querySelectorAll('.v-select__selection.v-select__selection--comma')
      this.models = []
      selects.forEach((item) => {
        this.models.push(item.innerHTML)
      })
    }
  }
}
</script>
<style scoped lang="scss">
.info {
  position: fixed;
  top: 0;
  left: 0;
  padding: 15px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  width: 100vw;
  z-index: 10;

  &-block {
    width: 20%;
    padding: 0 1%;

    &__title {
      margin-bottom: 0 !important;
    }
  }

  &::v-deep {
    .v-text-field__details {
      display: none;
    }

    .v-text-field {
      padding-top: 0;
      margin-top: 0;
    }
  }
}
</style>
