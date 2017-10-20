<template>
  <section class="container dev">
    <div>
      <BLVNKHeader/>
      <BLVNKNav/>
      <BLVNKContent prop:page="Abilities"/>
      <BLVNKFooter/>
    </div>
  </section>
</template>

<script>
import BLVNKHeader from '~/components/BLVNKHeader'
import BLVNKNav from '~/components/BLVNKNav'
import BLVNKContent from '~/components/BLVNKContent'
import BLVNKFooter from '~/components/BLVNKFooter'

export default {
  components: {
    BLVNKHeader,
    BLVNKNav,
    BLVNKContent,
    BLVNKFooter
  }
}
</script>