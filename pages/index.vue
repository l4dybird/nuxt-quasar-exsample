<script setup lang="ts">
import { ref } from '@nuxtjs/composition-api';
import Tutorial from '~/components/Tutorial.vue';

const name = ref(null);
const age = ref(null);
const accept = ref(false);
const refName = ref();
const refAge = ref();
const refAccept = ref();
const refFrom = ref();
const onSubmit = () => {
  console.log('click');
};

const onValidate = (): void => {
  refFrom .value.$children.map(
    (e: { validate?: any; }) => Object.keys(e).includes('validate') ? e.validate() : ''
  );
};

const onReset = () => {
    name.value = null
    age.value = null
    accept.value = false
};

const onHogeClick = (payload: string): void => {
  console.log(payload);
}
</script>

<template>
  <Tutorial @hoge="onHogeClick" />
</template>