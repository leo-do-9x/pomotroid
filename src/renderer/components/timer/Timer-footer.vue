<template>
  <section class="Container Footer">
    <div class="Round-wrapper">
      <p>
        {{ round + '/' + workRounds }}
        <span
          v-if="totalWorkRounds > 0"
          class="Total-rounds"
          title="Focus rounds completed"
          >({{ totalWorkRounds }})</span
        >
      </p>
      <p class="TextButton" title="Reset current round" @click="callForReset">
        Reset
      </p>
    </div>
  </section>
</template>

<script>
import { EventBus } from '@/utils/EventBus'

export default {
  name: 'TimerFooter',
  computed: {
    // store getters
    currentRound() {
      return this.$store.getters.currentRound
    },

    round() {
      return this.$store.getters.round
    },

    workRounds() {
      return this.$store.getters.workRounds
    },

    totalWorkRounds() {
      return this.$store.getters.totalWorkRounds
    }
  },

  methods: {
    callForReset() {
      EventBus.$emit('call-timer-reset')
    }
  }
}
</script>

<style lang="scss" scoped>
.Footer {
  align-items: center;
  display: flex;
  justify-content: center;
}
</style>
