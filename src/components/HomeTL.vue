<template>
    <LayoutPo>
      <template #header>
        <HeaderQa></HeaderQa>
      </template>
      <template #resume>
        <Resume
          :total-label="'Ahorro total'"
          :label="label"
          :total-amount="1000000"
          :amount="amount"
        >
          <template #graphic>
            <GrapHic :amounts="amounts" />
          </template>
          <template #action>
            <ActionZx />
          </template>
        </Resume>
      </template>
      <template #movements>
        <Movements :movements="movements" />
      </template>
    </LayoutPo>
  </template>
  
  <script>
  import LayoutPo from "./LayoutPo.vue";
  import HeaderQa from "./HeaderQa.vue";
  import Resume from "./Resume/IndexWe.vue";
  import ActionZx from "./ActionZx.vue";
  import Movements from "./Movements/IndexHe.vue";
  import GrapHic from "./Resume/GrapHic.vue";
  
  export default {
    components: {
      LayoutPo,
      HeaderQa,
      Resume,
      ActionZx,
      Movements,
      GrapHic,
  },
    data() {
      return {
        label: null,
        amount: null,
        movements: [
          {
            id: 0,
            title: "Movimiento 1",
            description: "Lorem ipsum dolor sit amet",
            amount: 100,
            time: new Date("02-01-2022"),
          },
          {
            id: 1,
            title: "Movimiento 2",
            description: "Lorem ipsum dolor sit amet",
            amount: 200,
            time: new Date("02-01-2022"),
          },
          {
            id: 2,
            title: "Movimiento 3",
            description: "Lorem ipsum dolor sit amet",
            amount: 500,
            time: new Date("02-01-2022"),
          },
          {
            id: 3,
            title: "Movimiento 4",
            description: "Lorem ipsum dolor sit amet",
            amount: 200,
            time: new Date("02-01-2022"),
          },
          {
            id: 4,
            title: "Movimiento 5",
            description: "Lorem ipsum dolor sit amet",
            amount: -400,
            time: new Date("02-01-2022"),
          },
          {
            id: 5,
            title: "Movimiento 6",
            description: "Lorem ipsum dolor sit amet",
            amount: -600,
            time: new Date("02-01-2022"),
          },
          {
            id: 6,
            title: "Movimiento 7",
            description: "Lorem ipsum dolor sit amet",
            amount: -300,
            time: new Date("02-01-2022"),
          },
          {
            id: 7,
            title: "Movimiento 8",
            description: "Lorem ipsum dolor sit amet",
            amount: 100,
            time: new Date("02-01-2022"),
          },
          {
            id: 8,
            title: "Movimiento 9",
            description: "Lorem ipsum dolor sit amet",
            amount: 300,
            time: new Date("01-01-2022"),
          },
          {
            id: 9,
            title: "Movimiento 10",
            description: "Lorem ipsum dolor sit amet",
            amount: 500,
            time: new Date("01-01-2022"),
          },
        ],
      };
    },
    computed: {
      amounts() {
        const lastDays = this.movements
          .filter(m => {
            const today = new Date();
            const oldDate = today.setDate(today.getDate() - 30);
  
            return m.time > oldDate;
          })
          .map(m => m.amount);
        
        return lastDays.map((m, i) => {
          const lastMovements = lastDays.slice(0, i);
  
          return lastMovements.reduce((suma, movement) => {
            return suma + movement
          }, 0);
        });
      }
    },
  };
  </script>