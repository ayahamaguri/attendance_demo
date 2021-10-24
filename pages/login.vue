<template>
  <div>
    <v-form>
      <v-container
        ><v-row
          ><v-col cols="2"> <v-subheader>メールアドレス</v-subheader></v-col>
          <v-col cols="6">
            <v-text-field
              clearable
              label="例：pt11001@stud.tumh.ac.jp"
            ></v-text-field></v-col></v-row
        ><v-row
          ><v-col cols="2"><v-subheader>パスワード</v-subheader></v-col
          ><v-col cols="6"
            ><v-text-field clearable></v-text-field></v-col></v-row
        ><v-btn color="orange">ログイン</v-btn></v-container
      >
    </v-form>
  </div>
</template>
