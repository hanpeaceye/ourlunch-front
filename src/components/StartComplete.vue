<template>
  <div>
    <SubTitle class ="title1">축하합니다! {{ getLoginUser.name }}님</SubTitle>
    <SubTitle class ="title2">점심팸 등록 완료!</SubTitle>

      <div class ="buttons">
          <Button class="primary" @click="gotoMain()">우리의점심 시작</Button>
      </div>
  </div>
</template>

<script>
import Button from '@/components/ui/Button'
import SubTitle from '@/components/ui/SubTitle'
import Input from '@/components/ui/Input'
import { mapGetters } from 'vuex'

export default {
  name: 'StartComplete',
  mounted: function () {
    if (!this.getLoginUser.isLogined) {
      this.$router.push('login')
    }
    if (!this.getLoginUser.isFullAuth) {
      this.$router.push('./')
    }
  },
  computed: {
    ...mapGetters([
      'getLoginUser'
    ])
  },
  components: {
    SubTitle, Input, Button
  },
  methods: {
    gotoMain: function () {
      this.$router.push('main')
    }
  }
}
</script>

<style scoped>

button.base_button.primary {
  width: 65%;
}

.title2 {
  margin-bottom: 50px;
}

.buttons {
  width: 100%;
  position: fixed;
  bottom: 50px;
}
</style>
