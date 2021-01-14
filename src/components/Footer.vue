<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__inner">
        <Logo/>
        <Nav/>
        <Contacts/>
      </div>
    </div>
  </footer>
</template>

<script>
import Logo from "@/components/Logo";
import Nav from "@/components/Nav";
import Contacts from "@/components/Contacts";
export default {
  name: "Footer",
  components: {Contacts, Nav, Logo}
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";

  .footer {
    flex-shrink: 0;
    padding: 18px 0;
    background-color: $bg-dark;
    margin-top: auto;
  }

  .footer__inner {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
  }
</style>
