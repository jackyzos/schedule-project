<template lang="html">
  <div class="container">
    <div class="field">
  <p class="control has-icons-left has-icons-right">
    <input class="input" type="email" placeholder="Email">
    <span class="icon is-small is-left">
      <i class="fas fa-envelope"></i>
    </span>
    <span class="icon is-small is-right">
      <i class="fas fa-check"></i>
    </span>
  </p>
</div>
<div class="field">
  <p class="control has-icons-left">
    <input class="input" type="password" placeholder="Password">
    <span class="icon is-small is-left">
      <i class="fas fa-lock"></i>
    </span>
  </p>
</div>
<div class="field">
  <p class="control">
    <a href="#/user/Username" class="button is-success">Login As User</a>
    <a href="#/admin/Username" class="button is-danger">Login As Admin</a>
  </p>
</div>

  </div>

</template>

<script>
export default {
}
</script>

<style lang="css" scoped>
.container{
  width: 50%;
  padding-top: 25px;
}
</style>
