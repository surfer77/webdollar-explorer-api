<template>
  <div >

    <div v-if="miner" class="minerTable">

      <h2>Address Details</h2>

      <div>
          <span>
            Address
          </span>
        <span>
            <a :href="'#/miner/' + miner.address">{{ miner.address }}</a>
          </span>
      </div>

      <div v-if=" miner.balance !== 0" >
          <span >
            Current balance
          </span>
        <span>
            {{ this.formatMoneyNumber(miner.balance*10000,2) }}
          </span>
      </div>

      <div v-if="miner.miner_balance !== 0">
          <span>
            Total Mined amount
          </span>
        <span>
            <!--TODO add fee to mined amount-->
            {{ this.formatMoneyNumber(miner.miner_balance*10000,2) }}
          </span>
      </div>

      <div v-if="miner.trx_to_balance !== 0" >
          <span>
            Transactions sent amount
          </span>
        <span>
            {{ this.formatMoneyNumber(miner.trx_to_balance*10000,2) }}
          </span>
      </div>

      <div v-if="miner.trx_from_balance !== 0">
          <span>
            Transactions received amount
          </span>
        <span>
            {{ this.formatMoneyNumber(miner.trx_from_balance*10000,2) }}
          </span>
      </div>

      <div v-if="miner.blocks && miner.blocks.length" >
          <span>
            Blocks mined
          </span>
        <span>
            {{ miner.blocks.length }}
          </span>
      </div>

      <div v-if="miner.transactions && miner.transactions.length" >
          <span>
            Transactions
          </span>
        <span>
            {{ miner.transactions.length }}
          </span>
      </div>

    </div>

    <div v-else>
      There are no blocks <br /><br />
    </div>

  </div>

</template>

<script>

import Utils from '@/services/utils'
import BlocksService from '@/services/BlocksService'

export default {
  name: 'block',

  props:{
    miner:{ default:()=>{return [] }},
  },

  methods: {

    formatMoneyNumber(number, decimals){
      return Utils.formatMoneyNumber(number, decimals);
    }
  }

}
</script>
<style type="text/css">

  .result{
    display: block;
    padding: 10px 0;
  }

  .blockContainer{
    border:solid 1px #5f5f5f;
    text-align: center;
    width: 600px;
    margin: 0 auto;
  }

  .title{
    border-bottom:solid 1px #5f5f5f;
  }

  .textTitle{
    width: 100%;
    background-color: #3a3a3a;
    box-sizing: border-box;
    padding: 10px 0;
    display: block;
  }

</style>
