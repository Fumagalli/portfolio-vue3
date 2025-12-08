<!-- React Hook equivalente -->
<!-- const { t } = useTranslation(); -->

<!-- Vue 3 Composition API -->
<script setup lang="ts">
import { useI18n } from 'vue-i18n'

const { t } = useI18n()
</script>

<!-- Binding de eventos -->
<!-- React: onClick={handler} -->
<!-- Vue: @click="handler" -->

<!-- Conditional rendering -->
<!-- React: {condition && <Component />} -->
<!-- Vue: <Component v-if="condition" /> -->

<!-- Loop -->
<!-- React: {items.map(item => <Component :key={item.id} />)} -->
<!-- Vue: <Component v-for="item in items" :key="item.id" /> -->
