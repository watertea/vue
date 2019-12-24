<template>
  <el-container class="layout-default">
    <el-header height='197px'>
      <my-header/>
    </el-header>
    <el-main>
      <nuxt/>
    </el-main>
    <el-footer height='auto'>
      <my-footer/>
    </el-footer>
  </el-container>
</template>
<script>
import myHeader from '@/components/public/header';
import myFooter from '@/components/public/footer'
export default {
  components:{
    myHeader,
    myFooter
  }
}
</script>

