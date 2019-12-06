<template>
  <div class="dashboard-container">
    <div class="dashboard-text">name: {{ name }}</div>
    <div class="dashboard-text">roles: <span v-for="role in roles" :key="role">{{ role }}</span></div>
    <div v-if="resources.includes('addUser')">Add User</div>
    <div v-permission="['addUser']">Add User</div>
    <div v-if="resources.includes('editUser')">Edit User</div>
    <div v-permission="['editUser']">Edit User</div>
    <div v-if="resources.includes('removeUser')">Remove User</div>
    <div v-permission="['removeUser']">Remove User</div>
    <div v-if="resources.includes('addRole')">Add Role</div>
    <div v-permission="['addRole']">Add Role</div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import permission from '@/directive/permission/index.js' // 权限判断指令

export default {
  name: 'Dashboard',
  directives: { permission },
  computed: {
    ...mapGetters([
      'name',
      'roles',
      'resources'
    ])
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
