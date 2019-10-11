<template>
    <div>
     <div v-for="(pic,index) in pictures" :key=index>
        <div class="content">
            <div class="content-title">
                <h2>{{pic.title}}</h2>
            </div>
            <div class="content-fill">
                <div><img :src=pic.img alt=""></div>
                <div class="footer-content">
                    <a href="http://www.facebook.com/sharer.php?u=<masukin url gambar disini>" target="_blank">
                    <img src="https://simplesharebuttons.com/images/somacro/facebook.png" alt="Facebook" />
                    <a href="mailto:?Subject=Simple Share Buttons&amp;Body=I%20saw%20this%20and%20thought%20of%20you!%20 <masukin url gambar disini>">
                    <img src="https://simplesharebuttons.com/images/somacro/email.png" alt="Email" /></a>
                </div>
                </div>
        </div>
    </div>
    </div>
</template>

<script>


</script>


<style>

.content-title h2 {
    margin-bottom: 15px;
}

.content-fill {
    display: flex;
    flex-direction: column;
}

</style>