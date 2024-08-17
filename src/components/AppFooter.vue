<template>
  <footer>
    <div class="footer-container">
      <img src="../assets/logo.png" alt="Company Logo" class="footer-logo" />
    </div>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter'
}
</script>

<style scoped>
footer {
  margin-top:20px;
  background: #043953;
  height:400px;
  padding: 20px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.footer-logo {
  height: 60px;
  width:120px;
}
</style>
