<template>
  <div>
    {{ dateInWords }}<q-tooltip>{{ tooltipContent }}</q-tooltip>
  </div>
</template>

<script>
import { QTooltip } from 'quasar'

import dateFnsHelper from '@/services/dateFnsHelper'

export default {
  props: {
    date: {
      type: Date | String, // TODO remove string, always convert to date before
      required: true,
    },
  },
  components: { QTooltip },
  computed: {
    tooltipContent () {
      return this.$d(new Date(this.date), 'long')
    },
    dateInWords () {
      return dateFnsHelper.distanceInWordsToNow(this.date, { addSuffix: true, disallowFuture: true })
    },
  },
}
</script>
