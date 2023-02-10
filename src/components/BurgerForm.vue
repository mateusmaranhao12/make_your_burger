<template>
    <Message :msg="msg" v-show="msg" />
    <div>
      <form id="burger-form" method="POST" @submit="createBurger">
        <div class="input-container">
          <label for="nome">Nome do cliente:</label>
          <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
        </div>
        <div class="input-container">
          <label for="pao">Escolha o pão:</label>
          <select name="pao" id="pao" v-model="pao">
            <option value="">Selecione o seu pão</option>
            <option value="integral">Integral</option>
          </select>
        </div>
        <div class="input-container">
          <label for="carne">Escolha a carne do seu Burger:</label>
          <select name="carne" id="carne" v-model="carne">
            <option value="">Selecione o tipo de carne</option>
            <option value="maminha">Maminha</option>
            <option value="alcatra">Alcatra</option>
          </select>
        </div>
        <div id="opcionais-container" class="input-container">
          <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
          <div class="checkbox-container">
            <input type="checkbox" name="opcionais" v-model="opcionais" value="ovo">
            <span>Ovo</span>
          </div>
          <div class="checkbox-container">
            <input type="checkbox" name="opcionais" v-model="opcionais" value="barbecue">
            <span>Barbecue</span>
          </div>
          <div class="checkbox-container">
            <input type="checkbox" name="opcionais" v-model="opcionais" value="cheddar">
            <span>Cheddar</span>
          </div>
        </div>
        <div class="input-container">
          <input class="submit-btn" type="submit" value="Criar meu Burger!">
        </div>
      </form>
    </div>
  </template>

<script>
    export default {
        name: 'BurgerForm'
    }
</script>

<style lang="scss">
    @import '@/scss/index';
</style>