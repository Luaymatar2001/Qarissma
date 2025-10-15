<script setup>
 
import { ref, onMounted } from 'vue';

const isOpen = ref(false);
const isHidden = ref(false);

onMounted(() => {
  // بعد تحميل الصفحة، نفتح الستارة بعد ثانية
  setTimeout(() => {
    isOpen.value = true;

    // بعد 2 ثانية من فتحها، نخفيها
    setTimeout(() => {
      isHidden.value = true;
    }, 2000);
  }, 700);
});

function restartCurtain() {
  isHidden.value = false;
  isOpen.value = false;

  setTimeout(() => {
    isOpen.value = true;
    setTimeout(() => {
      isHidden.value = true;
    }, 2000);
  }, 500);
}
   
</script>

<template>
    <div>
        <!-- ستارة البداية -->
        <div class="curtain" :class="{'open': isOpen, 'fade-out': isHidden}">
            <div class="curtain__panel curtain__panel--left"></div>
            <div class="curtain__panel curtain__panel--right"></div>
        </div>

        <div class="content">
            <!-- <img class="logos logo mx-auto mb-4 " src="/public/images/CurtineBackground.jpg" alt="butterflies background" /> -->

            <div class="content-text">
                <div class="flex justify-center">
                    <img class="butterflies-bg"
                        src="../../public/images/freepik__a-minimalist-luxury-cafe-encased-in-a-transparent-__73947.png" alt="">
                </div>
                <p class="text-lg md:text-xl font-light leading-relaxed mb-8">Create an account to get full access to unlimited resources</p>
                <div class="flex flex-col sm:flex-row gap-6 justify-center mt-4">
                    <button class="btn-primary">
                        Get started now
                    </button>

                    <button class="btn-secondary">
                        Sign in
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

/* 🟥 الستارة */
.curtain {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: 10;
    display: flex;
}

.curtain__panel {
    flex: 1;
    background-image: url("https://images.vexels.com/media/users/17482/101168/preview2/01bdac45c37aff22f75230abf3f019d4-red-curtain-background.png");
    background-repeat: no-repeat;
    background-size: cover;
    transition: transform 2s ease-out;
}

.curtain__panel--left {
    transform: translateX(0);
}

.curtain__panel--right {
    transform: translateX(0);
}

.curtain.open .curtain__panel--left {
    transform: translateX(-100%);
}

.curtain.open .curtain__panel--right {
    transform: translateX(100%);
}

.fade-out {
    opacity: 0;
    transition: opacity 1s ease-out;
    pointer-events: none;
}

/* 🦋 خلفية الفراشات */
.logos {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    opacity: 0.20;
    /* خافت */
    z-index: 0;
}

/* 🎬 المحتوى */
.content {
    position: relative;
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: white;
    z-index: 1;
    
}

.content-text {
    z-index: 2;
    text-align: center;
    text-shadow: 0 0 10px rgba(0, 0, 0, 0.6);
    animation: fadeInUp 1s ease-out 2.5s both;
}

.content h1 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
}

.content p {
    font-size: 1.2rem;
    margin-bottom: 1.5rem;
}

.btn-primary {
    padding: 12px 40px;
    border: none;
    border-radius: 25px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: #fff;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
    transition: all 0.3s ease;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.btn-primary:hover {
    background: linear-gradient(135deg, #764ba2 0%, #667eea 100%);
    box-shadow: 0 6px 20px rgba(102, 126, 234, 0.6);
    transform: translateY(-2px);
}

.btn-secondary {
    padding: 12px 40px;
    border: 2px solid #fff;
    border-radius: 25px;
    background: transparent;
    color: #fff;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(255, 255, 255, 0.1);
    transition: all 0.3s ease;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.btn-secondary:hover {
    background: rgba(255, 255, 255, 0.1);
    box-shadow: 0 6px 20px rgba(255, 255, 255, 0.2);
    transform: translateY(-2px);
}

.content .butterflies-bg  {
    justify-content: center;
    margin-bottom: 100px;
    width: 170px;
    height: 170px;
    border-radius: 50%;
    border: 4px solid #fff;
    box-shadow: 0 0 15px rgba(243, 151, 151, 0.4);
    background: #fff;
    animation: float 3s ease-in-out infinite;
}

@media (max-width: 768px) {
    .content .butterflies-bg {
        width: 120px;
        height: 120px;
        margin-bottom: 50px;
    }

    .content p {
        font-size: 1rem;
        padding: 0 1rem;
    }

    .btn-primary,
    .btn-secondary {
        padding: 10px 30px;
        font-size: 1rem;
    }
}

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes float {
    0%, 100% {
        transform: translateY(0px);
    }
    50% {
        transform: translateY(-10px);
    }
}
</style>