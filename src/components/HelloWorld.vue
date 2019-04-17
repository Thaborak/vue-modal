<template>
  <v-container fill-height fluid>
    <v-layout text-xs-center wrap justify-center>
      <v-flex align-self-center justify-center xs12>
        <v-dialog
          hide-overlay
          no-click-animation
          v-model="dialog"
          :fullscreen="$vuetify.breakpoint.smAndDown" 
          max-width="80vw"
        >
          <template v-slot:activator="{ on }">
            <button v-on="on" class="item">
              <span>ADD TO CART</span>
            </button>
          </template>
          <v-card flat>
            <v-toolbar flat>
              <v-flex>
                <v-toolbar-title class="underlined-header-wrapper">
                  <span class="underlined-header" style>Want to add one of these?</span>
                </v-toolbar-title>
              </v-flex>

              <v-spacer></v-spacer>
              <v-btn icon @click="dialog = false">
                <img
                  src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAoCAYAAACM/rhtAAABiElEQVRYw9WYu23DMBBA7UKllnCjMdQb6cUVUmYBzWEI0AQC1HiNIEGKwH2SJvEEgQUod8YJYBRSJikquiteY/COTyZ5/Gzu7h82nAkKenp+2QIZUAAlUAENcCQa+q2kNth2u7ggdJICCqg1GVdqik2jC0LShJI3AWJjGsqVRBGERDvgEEFsDObczRKEBDnQLiA3gLnzIEEI3C8oNmbvJUj/3PGfyZ0Eac61Kwi2pjlpWq2HFeT0hZNMCSpb8Nv7x2PXdd/A5fPr/OrbOcZgLObAXBNtlVGQirC1zpFcPwAdnjzkTnos5rpRJ1OToJrqhL6+95U0yCGXG3HqlyDtrbXDEPU+kha53mGK1MPePQhmgUNllfRpayHTBYsZ8+lPxxHkkEIXLD1XpFUgkhxS6oJVQNkwikSSQypdMOgY5SIZKHctN7pgcPWfkpwhd0WUIPshZr9I2JcZ9oWa/VbH+7DA/rgl4sDK/sgv4tLE/top4uIu4ulDxOORiOc3EQ+YIp6AxTyir8EPCd3y3dBAqCYAAAAASUVORK5CYII="
                  style="height: 20px; width: 20px;"
                  @click="dialog = false"
                >
              </v-btn>
            </v-toolbar>
            <span class="hidden-sm-and-down" style="padding-left: 20px;">
              Customers who bought the
              <b style="font-weight: 700 color: black">SPX1501</b> also bought these popular items:
            </span>

            <v-container light>
              <v-layout
                align-space-around
                justify-center
                row
                fill-height
                :column="$vuetify.breakpoint.smAndDown"
                :align-start-between="$vuetify.breakpoint.smAndDown"
              >
                <v-flex v-for="item in items" :key="item.id" md3>
                  <v-card flat>
                    <v-layout>
                      <!-- desktop modal -->
                      <v-card-text class="hidden-sm-and-down">
                        <v-flex :xs4="$vuetify.breakpoint.smAndDown">
                          <v-img contain v-bind:src="item.image"></v-img>
                        </v-flex>
                        <v-flex >
                          <span>
                            <b>{{ item.title }}</b>
                          </span>
                        </v-flex>
                        <v-flex>
                          <span>{{ item.code }}</span>
                        </v-flex>
                        <v-flex>
                          <span>{{ item.price }}</span>
                        </v-flex>
                        <v-btn
                          style="background: rgb(25, 70, 186);
                        border: rgb(25, 70, 186) 2px solid;
                        color: white;
                        font-weight: 700;
                        ma-0!important"
                          :pointer="$vuetify.breakpoint.smAndDown"
                        >ADD TO CART</v-btn>
                      </v-card-text>
                    </v-layout>
                    <!-- mobile fullscreen modal -->
                    <v-layout class="hidden-md-and-up mobile-border" fill-height>
                      <v-flex :xs9="$vuetify.breakpoint.smAndDown">
                        <v-img v-bind:src="item.image"></v-img>
                      </v-flex>
                      <v-card-text>
                        <v-flex>
                          <span>
                            <b>{{ item.title }}</b>
                          </span>
                        </v-flex>
                        <v-flex>
                          <span>{{ item.code }}</span>
                        </v-flex>
                        <v-flex>
                          <span>{{ item.price }}</span>
                        </v-flex>
                        <span class="addtobag">ADD TO CART</span>
                      </v-card-text>
                    </v-layout>
                  </v-card>
                </v-flex>
              </v-layout>
              <v-flex>
                <v-btn
                  style="background: rgb(25, 70, 186);
                        border: rgb(25, 70, 186) 2px solid;
                        color: white;
                        width: 100%;
                        font-weight: 700"
                  align-content-center
                >ADD THESE 4 ITEMS AND SAVE 10%</v-btn>
              </v-flex>

              <v-layout align-end justify-end row fill-height>
                <span class="pointer" @click="dialog = false">No Thanks</span>
                
                <button class="item" @click="dialog = false">
                  <span>Continue to Checkout</span>
                </button>
              </v-layout>
            </v-container>
          </v-card>
        </v-dialog>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      //store of items
      items: [
        {
          id: 1,
          image:
            "https://snowjoe.imgix.net/product-images/iON8024-XRP_Image01.jpg?auto=compress&fm=webp&w=700",
          title: "Cordless Two Stage Snow...",
          code: "ION8024-XRP",
          price: "$999.99"
        },
        {
          id: 2,
          image:
            "https://cdn.shopify.com/s/files/1/1711/8241/products/SPX3001_01.jpg?v=1525204252",
          title: "Electric Pressure Washer...",
          code: "SPX3001",
          price: "$179.99"
        },
        {
          id: 3,
          image:
            "https://cdn.shopify.com/s/files/1/1711/8241/products/SPX-APC1G-01.jpg?v=1524846777",
          title: "Heavy Duty Pressure Washe...",
          code: "SPX-APC1G",
          price: "$19.99"
        },
        {
          id: 4,
          image:
            "https://snowjoe.imgix.net/product-images/SJEG24_separate.jpg?auto=compress&fm=webp&w=700",
          title: "2-in-1 Snow Pusher + Ice Chop...",
          code: "SJEG24",
          price: "$29.99"
        }
      ]
    };
  }
};
</script>

<style>
.item {
  background: white;
  border: rgb(25, 70, 186) 2px solid;
  font-weight: 700;
  color: rgb(25, 70, 186);
  font-size: 16px;
  width: 33%;
  padding-top: 1%;
  padding-bottom: 1%;
}


.item:hover {
  background: rgb(25, 70, 186);
  border: rgb(25, 70, 186) 2px solid;
  color: white;
  font-weight: 700;
}

.pointer {
  cursor: pointer;
  border-bottom: 1px solid #333;
  margin-right: 30px;
  margin-bottom: 15px;
}

.addtobag {
  cursor: pointer;
  margin-right: 30px;
  margin-bottom: 15px;
}

.underlined-header-wrapper {
  width: 100%;
  border-bottom: 1px solid #333;
}
.underlined-header {
  border-bottom: solid;
  border-color: #1946ba;
  color: #333;
  font-weight: 100;
  line-height: 1.4;
  margin: 0;
  font-size: 36px;
  padding-left: 5px;
  border-bottom-width: 5px;
}

.resultContainer {
  height: 350px;
}

.mobile-border {
  border-bottom: black 1px solid;
  /* not sure if thats from the screenshot or not */
  /* border-left: black 1px solid; */
}

@media only screen and (max-width: 700px) {
  .underlined-header {
    font-size: 23px !important;
  }
}

@media only screen and (min-width: 1401px) {
  .vue-container {
    margin-left: auto;
    margin-right: auto;
    max-width: 1400px;
  }
}

@media only screen and (max-width: 1400px) and (min-width: 1100px) {
  .vue-container {
    margin-left: 3%;
    margin-right: 3%;
  }
}
@media only screen and (max-width: 1100px) and (min-width: 700px) {
  .vue-container {
    margin-left: 2%;
    margin-right: 2%;
  }
}
@media only screen and (max-width: 700px) {
  .vue-container:not(.nav-wrapper) {
    box-sizing: border-box;
    padding-left: 10px;
    padding-right: 10px;
  }
}
</style>

