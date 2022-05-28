<template>
  <div class="personal-main">
    <div class="personal-money">
      <h3><i>还款计划</i></h3>

      <div class="personal-moneylist" style="margin-top: 40px">
        <div class="pmain-contitle">
          <span class="pmain-title1 fb" style="width: 150px"> 还款编号 </span>
          <span class="pmain-title1 fb" style="width: 100px"> 还款金额 </span>
          <span class="pmain-title1 fb" style="width: 70px"> 年化利率 </span>
          <span class="pmain-title1 fb" style="width: 100px"> 状态 </span>
        </div>
        <ul>
          <li
            v-for="returnItem in returnList"
            :key="returnItem.id"
            style="width: 100%"
          >
            <span class="pmain-title1 pmain-height" style="width: 150px">
              {{ returnItem.returnNo }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ returnItem.total }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 70px">
              {{ returnItem.lendYearRate * 100 }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ returnItem.lendStatus }}
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
      this.$axios.$get('/web/core/lendReturn/list').then((response) => {
        this.returnList = response.data
      })
    },
  },
}
</script>
