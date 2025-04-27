<template>
    <header-store />
        <div class="breacrumb-section">
        <div class="container">
            <div class="row">
                <div class="col-lg-12 text-left">
                    <div class="breadcrumb-text product-more">
                        <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
                        <span>Shopping Cart</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <section class="shopping-cart spad">
        <div class="container">
            <div class="row">
                <div class="col-lg-8">
                    <div class="row">
                        <div class="col-lg-12">
                            <div class="cart-table">
                                <table>
                                    <thead>
                                        <tr>
                                            <th>Image</th>
                                            <th class="p-name text-center">Product Name</th>
                                            <th>Price</th>
                                            <th>Action</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr v-for="cart in userCart" :key="cart.id">
                                            <td class="cart-pic first-row">
                                                <img class="photo-item" :src="cart.photo" alt="" />
                                            </td>
                                            <td class="cart-title first-row text-center">
                                                <h5>{{ cart.name }}</h5>
                                            </td>
                                            <td class="p-price first-row">${{ cart.price }}</td>
                                            <td @click="removeItem(userCart.index)" class="delete-item"><a href="#"><i class="material-icons">
                                              close
                                              </i></a></td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                        <div class="col-lg-8 text-left">
                            <h4 class="mb-4">
                                Informasi Pembeli:
                            </h4>
                            <div class="user-checkout">
                                <form>
                                    <div class="form-group">
                                        <label for="namaLengkap">Nama lengkap</label>
                                        <input type="text" class="form-control" id="namaLengkap" aria-describedby="namaHelp" placeholder="Masukan Nama" v-model="csutomerInfo.name">
                                    </div>
                                    <div class="form-group">
                                        <label for="namaLengkap">Email Address</label>
                                        <input type="email" class="form-control" id="emailAddress" aria-describedby="emailHelp" placeholder="Masukan Email" v-model="csutomerInfo.email">
                                    </div>
                                    <div class="form-group">
                                        <label for="namaLengkap">No. HP</label>
                                        <input type="text" class="form-control" id="noHP" aria-describedby="noHPHelp" placeholder="Masukan No. HP" v-model="csutomerInfo.number">
                                    </div>
                                    <div class="form-group">
                                        <label for="alamatLengkap">Alamat Lengkap</label>
                                        <textarea class="form-control" id="alamatLengkap" rows="3" v-model="csutomerInfo.address"></textarea>
                                    </div>
                                </form>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-4 text-left">
                    <div class="row">
                        <div class="col-lg-12">
                            <div class="proceed-checkout">
                                <ul>
                                    <li class="subtotal">ID Transaction <span>#SH12000</span></li>
                                    <li class="subtotal mt-3">Subtotal <span>${{ totalPrice }}.00</span></li>
                                    <li class="subtotal mt-3">Pajak <span>10%</span></li>
                                    <li class="subtotal mt-3">Total Biaya <span>${{ totalCost }}.00</span></li>
                                    <li class="subtotal mt-3">Bank Transfer <span>Mandiri</span></li>
                                    <li class="subtotal mt-3">No. Rekening <span>2208 1996 1403</span></li>
                                    <li class="subtotal mt-3">Nama Penerima <span>Shayna</span></li>
                                </ul>
                                <a @click="checkout()" href="#" class="proceed-btn">I ALREADY PAID</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <footer-store />
</template>

<script>
import HeaderStore from '@/components/HeaderStore.vue';
import FooterStore from '@/components/FooterStore.vue';
import axios from "axios";

export default {
    name: "ShoppingCart",
    components: {
        HeaderStore,
        FooterStore
    },
    data() {
    return {
      userCart: [],
      csutomerInfo: {
        name: '',
        email: '',
        number: '',
        address: ''
      }
    };
  },
  methods: {
    removeItem(index) {
      this.userCart.splice(index, 1);
      const parsed = JSON.stringify(this.userCart);
      localStorage.setItem("userCart", parsed);
    },
    checkout() {
        let productIds = this.userCart.map(function(product){
            return product.id
        });

        let checkoutData = {
            'name': this.csutomerInfo.name,
            'email': this.csutomerInfo.email,
            'number': this.csutomerInfo.number,
            'address': this.csutomerInfo.address,
            'transaction_total': this.totalCost,
            'transaction_status': "PENDING",
            'transaction_details': productIds,
        };

        axios
            .post("http://127.0.0.1:8000/api/checkout", checkoutData)
            .then(() => this.$router.push("success"))
            .catch(err => console.log(err));
    }
  },
  mounted() {
    if (localStorage.getItem("userCart")) {
      try {
        this.userCart = JSON.parse(localStorage.getItem("userCart"));
      } catch (error) {
        localStorage.removeItems("userCart");
      }
    }
  },
  computed: {
    totalPrice() {
      return this.userCart.reduce(function(items, data) {
        return items + data.price;
      }, 0);
    },
    taxSummary() {
        return (this.totalPrice * 10) / 100;
    },
    totalCost() {
        return this.totalPrice + this.taxSummary;
    }
  }
}
</script>