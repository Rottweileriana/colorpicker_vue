<template>
  <header>
    <h3>Color<span>Picker</span></h3>
  </header>
</template>

<script>
export default {
  name: 'header-nav',
  props: ['color']
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 60px;
  width: 218px;
  background: #171717;
}
h3 {
  color: #F3F3F3;
  font-size: 24px;
  font-weight: 300;
  text-transform: uppercase;
  margin: 0 auto;
}
h3 span {
  color: #FFCE00;
  font-weight: 900;
  margin: 0 auto;
}
.color {
  width: 25px;
  height: 25px;
  border: 1px dashed #F3F3F3;
  margin: 0 auto;
}
</style>