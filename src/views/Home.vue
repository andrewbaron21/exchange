<template>
  <div>
    <bounce-loader :loading="isLoading" :color="'#00B1FF'" size="100" />
    <px-assets-table v-if="!isLoading" :assets="assets" />
  </div>
</template>

<script>
import api from '@/api'
import PxAssetsTable from '@/components/PxAssetsTable'

export default {
  name: 'Home',

  components: { PxAssetsTable },

  data() {
    return {
      isLoading: false,
      assets: []
    }
  },

  created() {
    this.isload = true

    api.getAssets().then(assets => (this.assets = assets))
    .finally(()=> this.isload = false)
  }
}
</script>
