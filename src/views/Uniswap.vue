<template>
  <Page>
    <RCard v-if="isBrave">
      <a
        href="https://uniswap.exchange/swap?outputCurrency=0x7dE91B204C1C737bcEe6F000AAA6569Cf7061cb7"
        target="_blank"
        >Go to Uniswap</a
      >
    </RCard>
    <iframe
      v-else
      src="https://uniswap.exchange/swap?outputCurrency=0x7dE91B204C1C737bcEe6F000AAA6569Cf7061cb7"
      height="760px"
      width="100%"
      style="
        border: 0;
        margin: 0 auto;
        display: block;
        border-radius: 10px;
        max-width: 600px;
        min-width: 300px;
      "
    />
  </Page>
</template>

<script>
import Page from "@/components/layout/Page";
import { isBrave, referral } from "@/utils/tools";

export default {
  props: ["referral"],
  components: {
    Page
  },
  data() {
    return {
      isBrave: true
    };
  },
  async created() {
    if (this.$robonomics.account === null) {
      this.$store.dispatch("chain/accessAccount", false);
    }
    this.isBrave = await isBrave();
    if (
      document.referrer &&
      document.referrer.replace(/\/$/, "") !== window.location.origin
    ) {
      referral(this.referral, document.referrer);
    }
  }
};
</script>
