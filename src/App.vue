<template>
  <div class="cities">
    <div class="cities__top">
      <div class="cities__label">Введите название города</div>
      <input type="text"
             class="cities__input"
             placeholder="Поиск"
             v-model="search">
    </div>
    <ul class="cities__list">
      <li class="cities__item" v-for="city in cities">
        <a v-bind:href="city.url" class="cities__link">
          {{ city.name }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    allCities: jsArray,
    search: ''
  }),
  computed: {
    cities() {
      if (this.search.length > 1) {
        return this.allCities.filter(city => {
          return city.name.toLowerCase().indexOf(this.search.toLowerCase()) === 0;
        });
      } else {
        return this.allCities;
      }
    }
  }
}
</script>

<style lang="scss">
.cities {

  &__label {
    font-weight: 500;
    font-size: 15px;
    color: #333333;
    margin-bottom: 14px;
  }

  &__top {
    margin-bottom: 40px;
    @media (max-width: 767.98px) {
      margin-left: 30px;
      margin-right: 30px;
      margin-bottom: 30px;
    }
  }

  &__input {
    width: 100%;
    height: 54px;
    border: 1px solid #E9E9E9;
    box-shadow: inset 3px 3px 7px rgba(0, 0, 0, 0.12);
    border-radius: 7px;
    font-size: 14px;
    padding: 0 18px;
    box-sizing: border-box;
    outline: none;
  }

  &__list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    list-style: none;
    margin: 0;
    padding: 0;

    @media (max-width: 767.98px) {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  &__item {

    &:last-child{
      border-top-right-radius: 20px;
      border-bottom-right-radius: 20px;
    }

    @media (min-width: 768px) {
      &:nth-child(8n-7),
      &:nth-child(8n-6),
      &:nth-child(8n-5),
      &:nth-child(8n-4) {
        background: #F4F7FB;
      }

      &:nth-child(8n-7) {
        border-top-left-radius: 20px;
        border-bottom-left-radius: 20px;
      }

      &:nth-child(8n-4) {
        border-top-right-radius: 20px;
        border-bottom-right-radius: 20px;
      }
    }

    @media (max-width: 767.98px) {
      &:nth-child(4n-3),
      &:nth-child(4n-2) {
        background: #F4F7FB;
      }

      &:last-child{
        border-top-right-radius: 0;
        border-bottom-right-radius: 0;
      }
    }

  }

  &__link {
    display: block;
    padding: 8px 14px;
    font-size: 16px;
    color: #000000;

    &:hover {
      color: #f67402;
    }
  }

}
</style>
