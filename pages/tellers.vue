<template>
  <div>
    <CompanyWhyUs />
    <TellersStatistics />
    <TellersRegister />
    <HomeSubscribe is-tellers-page />
    <HomeFooter />
  </div>
</template>

<script>
import TellersStatistics from '@/components/pages/tellers/statistics'
import TellersRegister from '@/components/pages/tellers/register'
import CompanyWhyUs from '@/components/pages/company/why-us'
import HomeSubscribe from '@/components/pages/home/subscribe'
import HomeFooter from '@/components/pages/home/footer'
export default {
  components: {
    TellersStatistics,
    TellersRegister,
    CompanyWhyUs,
    HomeSubscribe,
    HomeFooter
  }
}
</script>
