<template>
  <Page>
    <ActionBar>
      <Label class="header" text="Расчет ХЕ" />
    </ActionBar>

    <StackLayout class="main">
      <TextField
        class="carb100"
        v-model="carb100"
        hint="углеводов на 100г, г"
        @textChange="onTextChange"
      />
      <TextField
        class="weight"
        v-model="weight"
        hint="вес товара, г"
        @textChange="onTextChange"
      />
      <FlexboxLayout class="total" justifyContent="space-around">
        <Label class="title" text="ХЕ:" />
        <Label class="rez" :text="carb" />
      </FlexboxLayout>
    </StackLayout>
  </Page>
</template>

<script lang="ts">
import Vue from "nativescript-vue";

export default Vue.extend({
  data() {
    return {
      carb100: "",
      weight: "",
      carb: "0.00",
    };
  },
  methods: {
    onTextChange() {
      const carb100 = +this.carb100 ?? 0;
      const weight = +this.weight ?? 0;
      this.carb = ((carb100 * weight) / 1000).toFixed(2);
    },
  },
});
</script>

<style scoped lang="scss">
.header {
  font-size: 20;
}
.main {
  padding: 20 80;
}
.carb100 {
  font-size: 16;
}
.weight {
  font-size: 16;
}
.total {
  padding: 40 60;
}
.title {
  font-size: 18;
}
.rez {
  font-size: 20;
}
</style>
