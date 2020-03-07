<template>
  <div class="headerTitle">
    <span>Books Store</span>
  </div>
</template>

<script>
export default {
  name: 'headerbook',
}
</script>
<style scoped lang="scss">
.headerTitle{
  display: flex;
  height: 100px;
  background-color: #503a9f;
  align-items: flex-end;
  padding: 0 15px;
  span{
    font-size: 45px;
    font-family: Arial;
    color: whitesmoke;
  }
}
</style>
