<template>
  <div>
    <div class="tile is-ancestor">
      <div class="tile is-parent">
        <div class="tile is-child box">
          <div class="tabs is-centered">
            <ul>
              <li
                :class="{ 'is-active': tab.active }"
                :key="t"
                v-for="(tab, t) in tabs"
              >
                <a @click="toggler(t)">
                  {{ tab.caption }}
                </a>
              </li>
            </ul>
          </div>
          <asphalt-content v-show="tabs[0].active" />
          <aggregates-bulk-gravity v-show="tabs[1].active" />
          <asphalt-gravity v-show="tabs[2].active" />
          <mixture-bulk-gravity v-show="tabs[3].active" /><br />
          <mixture-max-gravity v-show="tabs[3].active" />
        </div>
      </div>
      <div class="tile is-parent is-4">
        <div class="tile is-child box">
          <direct />
        </div>
      </div>
      <div class="tile is-parent is-4">
        <div class="tile is-child box">
          <derived />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import AggregatesBulkGravity from '@/components/AggregatesBulkGravity.vue'
import AsphaltContent from '@/components/AsphaltContent.vue'
import AsphaltGravity from '@/components/AsphaltGravity.vue'
import MixtureBulkGravity from '@/components/MixtureBulkGravity.vue'
import MixtureMaxGravity from '@/components/MixtureMaxGravity.vue'
import Direct from '@/components/Direct.vue'
import Derived from '@/components/Derived.vue'

export default {
  name: 'Index',

  components: {
    AggregatesBulkGravity,
    AsphaltContent,
    AsphaltGravity,
    MixtureBulkGravity,
    MixtureMaxGravity,
    Direct,
    Derived
  },

  data: () => ({
    tabs: [
      {
        caption: 'Contenidos',
        active: true
      },
      {
        caption: 'Agregados',
        active: false
      },
      {
        caption: 'Asflato',
        active: false
      },
      {
        caption: 'Mezcla',
        active: false
      }
    ]
  }),

  methods: {
    toggler(index) {
      for (let i in this.tabs) {
        this.tabs[i].active = false
      }
      this.tabs[index].active = true
    }
  }
}
</script>
