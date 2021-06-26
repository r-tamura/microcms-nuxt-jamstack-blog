<template>
  <CBox w="100%" p="4">
    <CList spacing="3" style-type="disc">
      <CListItem v-for="content in contents" :key="content.id">
        <nuxt-link :to="`/${content.id}`">
          {{ content.title }}
        </nuxt-link>
      </CListItem>
    </CList>
    <c-button>ボタン</c-button>
  </CBox>
</template>

<script>
import { CBox, CButton, CList, CListItem } from '@chakra-ui/vue'
export default {
  components: { CBox, CButton, CList, CListItem },
  async asyncData({ $microcms }) {
    const data = await $microcms.get({
      endpoint: 'blog',
    })
    return data
  },
}
</script>
