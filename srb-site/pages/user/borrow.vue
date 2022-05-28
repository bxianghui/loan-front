<template>
  <div class="personal-main">
    <div class="personal-money">
      <h3><i>借款记录</i></h3>

      <div class="personal-moneylist" style="margin-top: 40px">
        <div class="pmain-contitle">
          <span class="pmain-title1 fb" style="width: 150px"> 借款编号 </span>
          <span class="pmain-title1 fb" style="width: 150px"> 借款标题 </span>
          <span class="pmain-title1 fb" style="width: 100px"> 借款金额 </span>
          <span class="pmain-title1 fb" style="width: 70px"> 年化利率 </span>
          <span class="pmain-title1 fb" style="width: 150px"> 借款时间 </span>
          <span class="pmain-title1 fb" style="width: 100px"> 状态 </span>
        </div>
        <ul>
          <li
            v-for="returnItem in returnList"
            :key="returnItem.id"
            style="width: 100%"
          >
            <span class="pmain-title1 pmain-height" style="width: 150px">
              {{ returnItem.lendNo }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 150px">
              {{ returnItem.title }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ returnItem.amount }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 70px">
              {{ returnItem.lendYearRate * 100 }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 150px">
              {{ returnItem.lendStartDate }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ returnItem.param.status }}
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
      returnList: [],
    }
  },

  created() {
    this.fetchreturnList()
  },

  methods: {
    fetchreturnList() {
      this.$axios.$get('/web/core/lend/list').then((response) => {
        this.returnList = response.data
      })
    },
  },
}
</script>
