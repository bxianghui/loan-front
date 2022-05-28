<template>
  <div class="personal-main">
    <div class="personal-money">
      <h3><i>回款计划</i></h3>

      <div class="personal-moneylist" style="margin-top: 40px">
        <div class="pmain-contitle">
          <span class="pmain-title1 fb" style="width: 100px"> 回款金额 </span>
          <span class="pmain-title2 fb" style="width: 70px"> 年化利率 </span>
          <span class="pmain-title3 fb" style="width: 100px"> 是否延期 </span>
          <span class="pmain-title3 fb" style="width: 100px"> 状态 </span>
          <span class="pmain-title3 fb" style="width: 150px"> 回款时间 </span>
        </div>
        <ul>
          <li
            v-for="returnItem in returnList"
            :key="returnItem.id"
            style="width: 100%"
          >
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ returnItem.total }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 70px">
              {{ returnItem.lendYearRate * 100 }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ returnItem.overdueStr }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 100px">
              {{ returnItem.lendStatus }}
            </span>
            <span class="pmain-title1 pmain-height" style="width: 150px">
              {{ returnItem.realReturnTime }}
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
      this.$axios.$get('/web/core/lendItemReturn/list').then((response) => {
        this.returnList = response.data
      })
    },
  },
}
</script>
