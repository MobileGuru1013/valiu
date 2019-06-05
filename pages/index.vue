<template>
  <div>
    <HomeTopHeader />
    <HomeTopSlider />
    <HomeTestimonials />
    <HomeAvailableBanks />
    <HomeCalculateTransfer />
    <HomeHowWorks />
    <HomeWhyUs />
    <HomeGetValiu />
    <HomeSubscribe />
    <HomeFooter has-privacy-and-policy />
  </div>
</template>

<script>
import HomeTopHeader from '@/components/pages/home/top-header'
import HomeTopSlider from '@/components/pages/home/top-slider'
import HomeTestimonials from '@/components/pages/home/testimonials'
import HomeAvailableBanks from '@/components/pages/home/available-banks'
import HomeCalculateTransfer from '@/components/pages/home/calculate-transfer'
import HomeHowWorks from '@/components/pages/home/how-works'
import HomeWhyUs from '@/components/pages/home/why-us'
import HomeGetValiu from '@/components/pages/home/get-valiu'
import HomeSubscribe from '@/components/pages/home/subscribe'
import HomeFooter from '@/components/pages/home/footer'
export default {
  components: {
    HomeTopHeader,
    HomeTopSlider,
    HomeTestimonials,
    HomeAvailableBanks,
    HomeCalculateTransfer,
    HomeHowWorks,
    HomeWhyUs,
    HomeGetValiu,
    HomeSubscribe,
    HomeFooter
  }
}
</script>
