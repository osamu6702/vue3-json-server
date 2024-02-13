<script setup>
import { toast } from 'vue3-toastify';
import 'vue3-toastify/dist/index.css';

toast.info("Wellcome to Information Technology", {
  autoClose: 1500,
  position:toast.POSITION.TOP_CENTER
})

const notify = () => {
  toast.success("Successfull", {
    autoClose: 1500,
    position: toast.POSITION.TOP_CENTER
  })
  return notify
}

</script>

<template>
  <div class="container my-5">
    <div class="card shadow" style="width: 20rem;">
      <div class="card-header p-0">
        <img src="https://scontent.xx.fbcdn.net/v/t1.15752-9/420566590_893734672217524_7035407566878439411_n.jpg?stp=dst-jpg_p206x206&_nc_cat=107&ccb=1-7&_nc_sid=510075&_nc_eui2=AeHKARaVcIsbfQM1u22OCX1lV4ZW-PV80PxXhlb49XzQ_MhZOvdbEedOzhPjR8GZ89VTkBd4VkeUCvfELfms9-eR&_nc_ohc=hvChKD1b4AYAX-UZYN9&_nc_ad=z-m&_nc_cid=0&_nc_ht=scontent.xx&oh=03_AdQSnRHCVy1PtJFJQHFQl2Br5tT9dBtfXwmTfC66SBq3zA&oe=65F254F2" class="card-img-top"
          alt="img">
      </div>
      <div class="card-body">
        <h5 class="card-title">Marionette_Genetics</h5>
        <p class="card-text">Recommend Cannabis strain for you.</p>
        <a href="http://localhost:5173/wonders"  class="btn btn-primary" style="background: #ff006a "  @click="notify">Go to Mainpage</a>

      </div>
    </div>
  </div>


</template>
