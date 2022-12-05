<template>
  <div>
    <div class="main-header">
      <h1 class="title">Latest News</h1>
      <Sorting
          :reversed="reversedList"
          @toggle="toggleReverseList"
      />
    </div>
    <div class="cards-container">
      <Card
          v-for="card in sorted"
          :card="card"
          :key="card.id"
      >
      </Card>
    </div>
  </div>
</template>

<script>
import Card from "@/components/Card";
import Sorting from "@/components/Sorting";

export default {
  name: "Home",
  components: { Card, Sorting },
  props: {
    searchValue: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      cardsList: [
        {
          id: 1,
          title: 'First Title Lorem Ipsum Dolor Sit Amet',
          img: '/img/Rectangle3.jpg',
          date: '26.12.2021',
          source: 'CNN Indonesia',
          content: `Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc
          gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa
          tortor nibh nulla condimentum imperdiet scelerisque condimentum imperdiet scelerisque`,
          url: '#'
        },
        {
          id: 2,
          title: 'Second Title Lorem Ipsum Dolor Sit Amet',
          img: '/img/Rectangle4.jpg',
          date: '11.01.2022',
          source: 'CNN Indonesia',
          content: ` Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque...
          Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra.
          read more`,
          url: '#'
        },
        {
          id: 3,
          title: 'Third Title Lorem Ipsum Dolor Sit Amet',
          img: '/img/Rectangle3.jpg',
          date: '07.11.2021',
          source: 'CNN Indonesia',
          content: `Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc
          gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa
          tortor nibh nulla condimentum imperdiet scelerisque condimentum imperdiet scelerisque`,
          url: '#'
        },
        {
          id: 4,
          title: 'Fourth Title Lorem Ipsum Dolor Sit Amet',
          img: '/img/Rectangle4.jpg',
          date: '03.12.2021',
          source: 'CNN Indonesia',
          content: ` Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque...
          Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra.
          read more`,
          url: '#'
        },
        {
          id: 5,
          title: 'Fifth Title Lorem Ipsum Dolor Sit Amet',
          img: '/img/Rectangle3.jpg',
          date: '15.12.2021',
          source: 'CNN Indonesia',
          content: `Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc
          gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa
          tortor nibh nulla condimentum imperdiet scelerisque condimentum imperdiet scelerisque`,
          url: '#'
        },
        {
          id: 6,
          title: 'Six Title Lorem Ipsum Dolor Sit Amet',
          img: '/img/Rectangle4.jpg',
          date: '06.12.2021',
          source: 'CNN Indonesia',
          content: ` Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque...
          Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra.
          read more`,
          url: '#'
        },
        {
          id: 7,
          title: 'Seven Title Lorem Ipsum Dolor Sit Amet',
          img: '/img/Rectangle3.jpg',
          date: '11.12.2021',
          source: 'CNN Indonesia',
          content: `Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc
          gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa
          tortor nibh nulla condimentum imperdiet scelerisque condimentum imperdiet scelerisque`,
          url: '#'
        },
        {
          id: 8,
          title: 'Eight Title Lorem Ipsum Dolor Sit Amet',
          img: '/img/Rectangle4.jpg',
          date: '30.12.2021',
          source: 'CNN Indonesia',
          content: ` Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque...
          Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra.
          read more`,
          url: '#'
        }
      ],
      reversedList: false
    }
  },
  methods: {
    strToTimestamp(str) {
      const parts = str.split('.');
      return new Date(parts[2], Number(parts[1]) - 1, parts[0]).getTime()
    },
    toggleReverseList() {
      this.reversedList = !this.reversedList
    }
  },
  computed: {
    sorted() {
      let list = Object.assign([], this.cardsList)
      if(this.reversedList) list.sort((a, b) => this.strToTimestamp(a.date) - this.strToTimestamp(b.date))
      else list.sort((a, b) => this.strToTimestamp(b.date) - this.strToTimestamp(a.date))
      if(this.searchValue.length) list = list.filter(item => item.title.toLowerCase().includes(this.searchValue.toLowerCase()))
      return list
    }
  }
}
</script>

<style scoped lang="scss">
@import "src/assets/style/var";
 .main-header {
   display: flex;
   align-items: flex-end;
   justify-content: space-between;
   margin-bottom: 24px;
   @media (max-width: 375px) {
     margin-bottom: 16px;
   }
 }
 .title {
   margin: 0;
   font-size: 36px;
   font-family: $roboto;
   line-height: 40px;
   @media (max-width: 768px) {
     font-size: 24px;
     line-height: 28px;
   }
 }
 .cards-container {
   display: grid;
   grid-template-columns: repeat(4, 1fr);
   gap: 30px;
   row-gap: 72px;
   @media (max-width: 1100px) {
     justify-content: center;
     grid-template-columns: repeat(3, 1fr);
     gap: 20px;
     row-gap: 48px;
   }
   @media (max-width: 760px) {
     grid-template-columns: repeat(2, 1fr);
   }
   @media (max-width: 550px) {
     row-gap: 32px;
   }
 }
</style>