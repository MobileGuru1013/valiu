<template>
  <div>
    <CompanyHeader />
    <CompanySubHeader />
    <CompanyWhyUs />
    <CompanyStatistics />
    <CompanyAbout />
    <CompanyJoinTeam />
    <HomeFooter />
  </div>
</template>

<script>
import CompanySubHeader from '@/components/pages/company/sub-header'
import CompanyHeader from '@/components/pages/company/header'
import CompanyStatistics from '@/components/pages/company/statistics'
import CompanyJoinTeam from '@/components/pages/company/join-team'
import CompanyWhyUs from '@/components/pages/company/why-us'
import CompanyAbout from '@/components/pages/company/about'
import HomeFooter from '@/components/pages/home/footer'
export default {
  components: {
    CompanySubHeader,
    CompanyStatistics,
    CompanyJoinTeam,
    CompanyHeader,
    CompanyWhyUs,
    CompanyAbout,
    HomeFooter
  }
}
</script>
