<template>
  <div class="personal-main">
    <div class="personal-money">
      <h3><i>投资记录</i></h3>

      <div class="personal-moneylist" style="margin-top: 40px">
        <div class="pmain-contitle">
          <span class="pmain-title1 fb" style="width: 150px"> 投资编号 </span>
          <span class="pmain-title1 fb" style="width: 100px"> 投资金额 </span>
          <span class="pmain-title1 fb" style="width: 70px"> 年化利率 </span>
          <span class="pmain-title3 fb" style="width: 150px"> 投资时间 </span>
          <span class="pmain-title3 fb" style="width: 100px"> 预期收益 </span>
          <span class="pmain-title3 fb" style="width: 100px"> 实际收益 </span>
        </div>
        <ul>
          <li v-for="invest in investList" :key="invest.id" style="width: 100%">
            <span class="pmain-title1 pmain-height" style="width: 150px">
              {{ invest.lendItemNo }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ invest.investAmount }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 70px">
              {{ invest.lendYearRate * 100 }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 150px">
              {{ invest.investTime }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ invest.expectAmount }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ invest.realAmount }}
            </span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      investList: [],
    }
  },

  created() {
    this.fetchInvestList()
  },

  methods: {
    fetchInvestList() {
      this.$axios.$get('/web/core/lendItem/list').then((response) => {
        this.investList = response.data
      })
    },
  },
}
</script>
