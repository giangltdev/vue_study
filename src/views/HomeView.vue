<template>
  <h2 class="counter-title">{{appTitle}}</h2>
  <h3 class="counter-title">{{CounterData.title}}</h3>
  <div class="home">
    <button @click="decreaseCounter" class="btn">-</button>
    <span class="counter">{{CounterData.count}}</span>
    <button  @click="increaseCounter(1)" class="btn">+</button>
    <button  @click="increaseCounter(2)" class="btn">++</button>
  </div>

  <div class="this-counter">
    <p>This counter is {{oddOrEven}}</p>
  </div>

  <div class="edit-counter-title">
    <h3 class="eidt-title">Edit Counter Title</h3>
    <input v-model="CounterData.title" class="edit-input" type="text">

  </div>
</template>

<script setup>
  // Có thể sử dụng ref hoặc reactive
  // computed dùng để tính toán
import {ref, reactive, computed, watch, onBeforeMount, onMounted, onBeforeUnmount, onUnmounted, onActivated} from 'vue'
  /**
   * Sử dụng khi gọi với ref
  const counter = ref(0),
  counterTitle = ref('My counter')
  */

  const appTitle = "My Counter App"

  const CounterData = reactive({
    count: 0,
    title: "My Counter"
  })
  // const decreaseCounter = () => {
  const decreaseCounter = () => {
    /**
     *  Sử dụng khi gọi với ref
     counter.value--
     */
    CounterData.count--
  }

  const increaseCounter = (amount, e) => {
    console.log(e);
    console.log('amount: ', amount);
    /**
     *  Sử dụng khi gọi với ref
     counter.value++
     */
    //  CounterData.count++
    CounterData.count+=amount
  }

  /** Thực hiện tính toán bằng thư viện computed */
  const oddOrEven = computed(() => {
    if(CounterData.count % 2 === 0) return 'even'
    else return 'odd'
  })

  // const count = ref()

// Xử lý alert
  watch(() => CounterData.count, (newCount, oldCount) => {
    if(newCount === 20) {
      alert('Bạn đã đạt đến 20')
    }
    
  } )
// Xử lý kiển tra chuyển trang
  onBeforeMount(() => {
    console.log('onBeforeMount: ', onBeforeMount);
  })

  onMounted(() => {
    console.log('onMounted: ', onMounted);
  })

  onBeforeUnmount(() => {
    console.log('onBeforeUnmount: ', onBeforeUnmount);
  })

  onUnmounted(() => {
    console.log('onUnmounted: ', onUnmounted);
  })

  onActivated(() => {
    console.log('onActivated: ', onActivated);

  })

</script>
// <!-- Phương pháp truyền thống
// <script>
//   export default {
//     data() {
//       return {
//         counter: 0
//       }
//     },
//     methods: {
//       increaseCounter() {
//         this.counter++;
//       },
//       decreaseCounter() {
//         this.counter--;
//       }
//     }

//   }
// </script>
-->

<!--
// <script>
//  export default {
//   data() {
//     return {
//       count: 0
//     }
//   },
//   computed: {
//     myComputedproperty() {
//       // perform logic based on a data propety
//       return 'my result'
//     }
//   },
//   watch: {
//     count(newCount, oldCound) {
//       if (newCount == 20) alert ('to large')
//     }
//   },
//   mounted() {
//     // do stuff when component is loaded
//     console.log('mounted: ', mounted);
//   },
//   unUnmounted() {
//     console.log('unUnmounted: ', unUnmounted);
//     }
//  }
// </script>
-->

<style>
  .home {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 3rem;
  }
  .btn {
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
    border: 1px solid #eee;
  }
  .counter-title {
    text-align: center;
    margin-top: 40px;
  }
  .edit-counter-title {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 30px;
  }

  .edit-input {
    display: block;
    width: 500px;
    height: 50px;
    font-size: 18px;
  }

  .this-counter {
    text-align: center;
  }
</style>
