<template>
  <section>
    RWS
  </section>
</template>

<script>
// import Providers from "./Providers";

export default {
  components: {
    // Providers
  },
  data() {
    return {
      RWS: "",
      showApprove: false
    };
  },
  computed: {
    
  },
  watch: {
    
  },
  mounted() {
    this.$on("approve", (data) => {
      this.showApprove = data;
    });
    return this.fetchData();
  },
  methods: {
    async fetchData() {
      this.rws = "";
      // const rwsAddr = this.$robonomics.web3.utils.toChecksumAddress(
      //   await this.$robonomics.ens.addrRws(this.rwsName)
      // );
      
    }
  }
};
</script>
