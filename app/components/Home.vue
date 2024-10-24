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
        ref="firstInput"
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
      <Button class="clearBtn" text="Очистить" @tap="clearFields" />
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
    clearFields() {
      this.carb100 = '';
      this.weight = '';
      this.$refs.firstInput.nativeView.focus();
    },
  },
});
</script>

<style scoped lang="scss">
.main {
  padding: 20 80;
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
.clearBtn {
  border-radius: 8;
}
</style>
